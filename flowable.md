## 介绍

![image-20230917112108571](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171121673.png)

## 基础

### 创建ProcessEngine

![image-20230917130250276](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171302362.png)

### 部署流程定义

![image-20230917144447646](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171444712.png)

```java
<?xml version="1.0" encoding="UTF-8"?>
<definitions xmlns="http://www.omg.org/spec/BPMN/20100524/MODEL" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
             xmlns:flowable="http://flowable.org/bpmn"
             typeLanguage="http://www.w3.org/2001/XMLSchema" expressionLanguage="http://www.w3.org/1999/XPath"
             targetNamespace="http://www.flowable.org/processdef">
    <!-- -请假条流程图 -->
    <process id="vacationRequest" name="请假条流程" isExecutable="true">
        <!-- -流程的开始 -->
        <startEvent id="startEvent"/>
        <sequenceFlow sourceRef="startEvent" targetRef="approveTask"/>

        <!-- -流程的节点 -->
        <userTask id="approveTask" name="开始请假" flowable:candidateGroups="managers"/>
        <!-- -流程节点间的线条，上一个节点和下一个节点-->
        <sequenceFlow sourceRef="approveTask" targetRef="decision"/>

        <!-- -排他性网关 -->
        <exclusiveGateway id="decision"/>
        <!-- -同意时 -->
        <sequenceFlow sourceRef="decision" targetRef="holidayApprovedTask">
            <conditionExpression xsi:type="tFormalExpression">
                <![CDATA[${approved}]]>
            </conditionExpression>
        </sequenceFlow>
        <!-- -拒绝时 -->
        <sequenceFlow  sourceRef="decision" targetRef="rejectEnd">
            <conditionExpression xsi:type="tFormalExpression">
                <![CDATA[${!approved}]]>
            </conditionExpression>
        </sequenceFlow>

        <userTask id="holidayApprovedTask" flowable:assignee="${employee}" name="同意请假"/>
        <sequenceFlow sourceRef="holidayApprovedTask" targetRef="approveEnd"/>

        <endEvent id="approveEnd"/>
        <endEvent id="rejectEnd"/>
        <!-- -流程的结束 -->
    </process>
</definitions>
```

![image-20230917151523323](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171515401.png)

讲解一下repositoryservice、runtimeService、TaskService、HistorryService

在Flowable和类似的BPMN（Business Process Model and Notation）流程引擎中，有多个服务用于管理和执行业务流程。以下是这些服务的主要作用和用途：

1. `RepositoryService`（存储库服务）：
   - 主要功能：用于管理流程定义和部署。
   - 作用：
     - 部署流程定义：将业务流程的定义（通常使用BPMN或其他建模语言编写）部署到流程引擎中，以便执行。
     - 查询流程定义：查询已经部署的流程定义，以获取版本信息、流程图等。
     - 删除流程定义：删除不再需要的流程定义。
     - 挂起和激活流程定义：可以挂起或激活流程定义，挂起后无法启动新的流程实例，但已经运行中的实例不受影响。
     - 获取流程资源：用于获取流程定义的XML文件、流程图等资源。

2. `RuntimeService`（运行时服务）：
   - 主要功能：用于管理和执行流程实例的运行时操作。
   - 作用：
     - 启动流程实例：根据流程定义启动一个新的流程实例。
     - 查询流程实例和任务：查询和访问正在运行的流程实例和任务。
     - 流程变量操作：管理流程实例中的流程变量，可以设置、获取和删除变量。
     - 信号和消息触发：用于触发信号事件或消息事件，以启动、激活或中断流程。
     - 完成任务：完成用户任务，使流程向前推进。
     - 挂起和激活流程实例：可以挂起或激活特定流程实例，影响其执行。

3. `TaskService`（任务服务）：
   - 主要功能：用于管理用户任务。
   - 作用：
     - 查询和访问任务：用于查询和访问与用户任务相关的信息，如任务列表、任务详情等。
     - 分派任务：将任务分派给具体的用户或组。
     - 完成任务：执行任务所需的操作，通常由人工或系统完成。
     - 创建任务：创建新的用户任务，将其添加到流程实例中。
     - 获取和处理任务变量：管理任务的局部流程变量。

4. `HistoryService`（历史服务）：
   - 主要功能：用于访问和查询流程的历史数据。
   - 作用：
     - 查询历史流程实例和任务：获取已经完成的流程实例和任务的历史信息。
     - 查询历史活动：查看流程中每个活动的历史记录，包括开始事件、结束事件等。
     - 查询历史流程变量：访问流程实例中使用过的历史变量。
     - 查询历史任务实例：获取已完成任务的详细信息。
     - 查询历史活动实例：查看流程实例中的活动历史记录。

这些服务共同构成了一个完整的流程引擎，允许您管理、执行和监控业务流程。根据需要，您可以使用这些服务来与流程引擎进行交互，实现自动化、监控和优化业务流程。不同的服务提供了不同层次的抽象，以满足各种业务流程管理需求。

```java
 ProcessEngineConfiguration configuration = null;
    @Before
    public void before() {
        //后去ProcessEngineConfiguration对象
        configuration = new StandaloneProcessEngineConfiguration();
        //配置数据库的连接信息
        configuration.setJdbcDriver("com.mysql.cj.jdbc.Driver");
        configuration.setJdbcUrl("jdbc:mysql://localhost:3306/flowable-learn?serverTimezone=UTC");
        configuration.setJdbcUsername("root");
        configuration.setJdbcPassword("yzk");
        //如果数据库中的表结构不存在就新建
        configuration.setDatabaseSchemaUpdate(ProcessEngineConfiguration.DB_SCHEMA_UPDATE_TRUE);
    }


    /**
     * 部署流程
     */
    @Test
    public void testDeploy() {
        //创建processEngine对象
        ProcessEngine processEngine = configuration.buildProcessEngine();
        //获取RepositoryService
        RepositoryService repositoryService = processEngine.getRepositoryService();
        //完成流程的部署操作
        Deployment deploy = repositoryService.createDeployment()
                .addClasspathResource("vacationRequest.bpmn20.xml")//关联要部署的文件
                .name("请假流程")
                .deploy();
        System.out.println(deploy.getId());
        System.out.println(deploy.getName());
    }


    /**
     * 查询流程定义信息
     */
    @Test
    public void testDeployQuery() {
        ProcessEngine processEngine = configuration.buildProcessEngine();
        RepositoryService repositoryService = processEngine.getRepositoryService();
        /*ProcessDefinitionQuery processDefinitionQuery = repositoryService.createProcessDefinitionQuery();
        ProcessDefinition processDefinition = processDefinitionQuery.deploymentId("1").singleResult();*/
        ProcessDefinition processDefinition = repositoryService.createProcessDefinitionQuery()
                .deploymentId("1")
                .singleResult();
        System.out.println("processDefinition.getDeploymentId() = " + processDefinition.getDeploymentId());
        System.out.println("processDefinition.getName() = " + processDefinition.getName());
        System.out.println("processDefinition.getDescription() = " + processDefinition.getDescription());
        System.out.println("processDefinition.getId() = " + processDefinition.getId());
    }

    /**
     * 删除流程定义
     */
    @Test
    public void testDeployDelete() {
        ProcessEngine processEngine = configuration.buildProcessEngine();
        RepositoryService repositoryService = processEngine.getRepositoryService();
        /*删除部署流程，第一个参数是id，如果部署的流程已经启动了，就不允许删除*/
        //repositoryService.deleteDeployment("1");
        //第二参数是级联删除，如果流程启动了，也可以删除，相关的任务也会被删除
        repositoryService.deleteDeployment("1",true);
    }
```

### 启动流程实例

![image-20230917153622484](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171536570.png)

![image-20230917155006588](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171550625.png)

### 查看任务

```java
    /**
     * 测试任务查询
     */
    @Test
    public void testTaskQuery() {
        ProcessEngine processEngine = configuration.buildProcessEngine();
        TaskService taskService = processEngine.getTaskService();

        List<Task> list = taskService.createTaskQuery()
                .processDefinitionKey("vacationRequest")//指定查询流程编号
                .taskAssignee("zhangsan")//查询这个任务的处理人
                .list();
        for (Task task : list) {
            System.out.println("task.getProcessDefinitionId() = " + task.getProcessDefinitionId());
            System.out.println("task.getName() = " + task.getName());
            System.out.println("task.getAssignee() = " + task.getAssignee());
            System.out.println("task.getDescription() = " + task.getDescription());
            System.out.println("task.getId() = " + task.getId());
        }
    }
```

### 完成任务

![image-20230917162444285](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171624320.png)

![image-20230917162740185](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171627266.png)

![image-20230917162755632](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171627699.png)
```java
    /**
     * 完成任务
     */
    @Test
    public void testCompleteTask() {
        ProcessEngine processEngine = configuration.buildProcessEngine();
        TaskService taskService = processEngine.getTaskService();
        Task task = taskService.createTaskQuery()
                .processDefinitionKey("vacationRequest")
                .taskAssignee("zhangsan")
                .singleResult();
        //创建流程变量
        HashMap<String, Object> variables = new HashMap<>();
        variables.put("approved",false);
        //完成任务
        taskService.complete(task.getId(),variables);
    }
```

### 查看历史信息

![image-20230917163840232](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171638349.png)

```java
   /**
     * 获取流程任务的历史数据
     */
    @Test
    public void testHistory() {
        ProcessEngine processEngine = configuration.buildProcessEngine();
        HistoryService historyService = processEngine.getHistoryService();
        List<HistoricActivityInstance> list = historyService.createHistoricActivityInstanceQuery()
                .processDefinitionId("vacationRequest:1:12503")
                .finished()
                .orderByHistoricActivityInstanceEndTime().asc()
                .list();

        for (HistoricActivityInstance history : list) {
            System.out.println(history.getActivityName()+":"+history.getAssignee()+"---"
                    +history.getActivityId()+":"+history.getDurationInMillis()+"毫秒"
            );
        }
    }
```



## 流程设计器

### Flowable UI

![image-20230917172843489](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171728553.png)

![image-20230917173848247](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171738296.png)

![image-20230917173855116](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171738182.png)

![image-20230917174450987](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171744047.png)

![image-20230917174458130](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171744159.png)

![image-20230917174614547](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171746610.png)

![image-20230917174703334](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171747397.png)

![image-20230917193319687](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171933745.png)

![image-20230917193327663](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171933721.png)

![image-20230917193413161](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171934224.png)

![image-20230917194104661](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171941721.png)

![image-20230917194156643](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171942506.png)

![image-20230917194307035](https://cdn.jsdelivr.net/gh/yzk656/image/img/202309171943080.png)
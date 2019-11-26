# AGP 4 with Product Flavor Crash

A project showing an issue introduced in **AGP 4.0.0**, where running `./gradlew connectedCheck` on a module with any **product flavor** crashes:

```
> Task :app:connectedAndroidTest FAILED

FAILURE: Build failed with an exception.

* What went wrong:
A problem was found with the configuration of task ':app:connectedAndroidTest' (type 'AndroidReportTask').
> No value has been specified for property 'reportsDir'.

* Try:
Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Exception is:
org.gradle.internal.execution.WorkValidationException: A problem was found with the configuration of task ':app:connectedAndroidTest' (type 'AndroidReportTask').
        at org.gradle.internal.execution.steps.ValidateStep.execute(ValidateStep.java:71)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.lambda$execute$2(SkipEmptyWorkStep.java:78)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.execute(SkipEmptyWorkStep.java:78)
        at org.gradle.internal.execution.steps.SkipEmptyWorkStep.execute(SkipEmptyWorkStep.java:34)
        at org.gradle.internal.execution.steps.legacy.MarkSnapshottingInputsStartedStep.execute(MarkSnapshottingInputsStartedStep.java:39)
        at org.gradle.internal.execution.steps.LoadExecutionStateStep.execute(LoadExecutionStateStep.java:40)
        at org.gradle.internal.execution.steps.LoadExecutionStateStep.execute(LoadExecutionStateStep.java:28)
        at org.gradle.internal.execution.impl.DefaultWorkExecutor.execute(DefaultWorkExecutor.java:33)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.executeIfValid(ExecuteActionsTaskExecuter.java:174)
        at org.gradle.api.internal.tasks.execution.ExecuteActionsTaskExecuter.execute(ExecuteActionsTaskExecuter.java:166)
        at org.gradle.api.internal.tasks.execution.CleanupStaleOutputsExecuter.execute(CleanupStaleOutputsExecuter.java:109)
        at org.gradle.api.internal.tasks.execution.FinalizePropertiesTaskExecuter.execute(FinalizePropertiesTaskExecuter.java:46)
        at org.gradle.api.internal.tasks.execution.ResolveTaskExecutionModeExecuter.execute(ResolveTaskExecutionModeExecuter.java:62)
        at org.gradle.api.internal.tasks.execution.SkipTaskWithNoActionsExecuter.execute(SkipTaskWithNoActionsExecuter.java:57)
        at org.gradle.api.internal.tasks.execution.SkipOnlyIfTaskExecuter.execute(SkipOnlyIfTaskExecuter.java:56)
        at org.gradle.api.internal.tasks.execution.CatchExceptionTaskExecuter.execute(CatchExceptionTaskExecuter.java:36)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.executeTask(EventFiringTaskExecuter.java:77)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:55)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter$1.call(EventFiringTaskExecuter.java:52)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$CallableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:416)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$CallableBuildOperationWorker.execute(DefaultBuildOperationExecutor.java:406)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor$1.execute(DefaultBuildOperationExecutor.java:165)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:250)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.execute(DefaultBuildOperationExecutor.java:158)
        at org.gradle.internal.operations.DefaultBuildOperationExecutor.call(DefaultBuildOperationExecutor.java:102)
        at org.gradle.internal.operations.DelegatingBuildOperationExecutor.call(DelegatingBuildOperationExecutor.java:36)
        at org.gradle.api.internal.tasks.execution.EventFiringTaskExecuter.execute(EventFiringTaskExecuter.java:52)
        at org.gradle.execution.plan.LocalTaskNodeExecutor.execute(LocalTaskNodeExecutor.java:41)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:374)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$InvokeNodeExecutorsAction.execute(DefaultTaskExecutionGraph.java:361)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:354)
        at org.gradle.execution.taskgraph.DefaultTaskExecutionGraph$BuildOperationAwareExecutionAction.execute(DefaultTaskExecutionGraph.java:340)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.lambda$run$0(DefaultPlanExecutor.java:127)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.execute(DefaultPlanExecutor.java:191)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.executeNextNode(DefaultPlanExecutor.java:182)
        at org.gradle.execution.plan.DefaultPlanExecutor$ExecutorWorker.run(DefaultPlanExecutor.java:124)
        at org.gradle.internal.concurrent.ExecutorPolicy$CatchAndRecordFailures.onExecute(ExecutorPolicy.java:64)
        at org.gradle.internal.concurrent.ManagedExecutorImpl$1.run(ManagedExecutorImpl.java:48)
        at org.gradle.internal.concurrent.ThreadFactoryImpl$ManagedThreadRunnable.run(ThreadFactoryImpl.java:56)
Caused by: org.gradle.api.InvalidUserDataException: No value has been specified for property 'reportsDir'.
        ... 39 more
```

Running `./gradlew connected[BuildVariant]AndroidTest` directly is ok.

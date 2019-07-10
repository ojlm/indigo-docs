# 创建一个任务

![](./gif/job.gif)

## 1. 进入创建任务的界面
> ![](./images/create-a-job-start.png)

## 2. 添加独立的请求

> ![](./images/create-a-job-filter.png)

## 3. 添加场景
> ![](./images/create-a-job-scenario.png)

## 4. 测试&创建
> ![](./images/create-a-job-test-new.png)

## 5. 添加触发器

### 简单类型
> ![](./images/create-a-job-trigger-simple.png)

### Cron 定时
> ![](./images/create-a-job-trigger-cron.png)

## 6. 添加订阅用户
> 任务执行完成后可以触发指定类型的通知事件
> ![](./images/create-a-job-subscriber.png)
> ![](./images/create-a-job-subscriber-types.png)

## 7. 通过API调用
> 任务都可以通过API调用，`http://host:port/api/ci/job/{jobId}`, `jobId` 参数填写生成的任务ID。

## 8. 查看报告
> 统计数据, 任务的历史趋势图
> ![](./images/create-a-job-report.png)

> 每次请求的详细数据
> ![](./images/create-a-job-report-item.png)

---
id: how-to-describe-a-scheduled-workflow-execution-in-python
title: How to describe a Scheduled Workflow Execution in Python
sidebar_label: Describe a Scheduled Workflow Execution
description: Use the `describe()` asynchronous method on the Schedule Handler.
tags:
- scheduled workflow execution
- schedules
- python sdk
- code sample
---

<!-- DO NOT EDIT THIS FILE DIRECTLY.
THIS FILE IS GENERATED from https://github.com/temporalio/documentation-samples-python/blob/main/schedule_your_workflow/describe_schedule_dacx.py. -->

To describe a Scheduled Workflow Execution in Python, use the [describe()](https://python.temporal.io/temporalio.client.ScheduleHandle.html#delete) asynchronous method on the Schedule Handle.
You can get a complete list of the attributes of the Scheduled Workflow Execution from the [ScheduleDescription](https://python.temporal.io/temporalio.client.ScheduleDescription.html) class.

:::copycode Sample application code

The following code sample comes from a working and tested sample application.
The code sample might be abridged within the guide to highlight key aspects.
Visit the source repository to [view the source code](https://github.com/temporalio/documentation-samples-python/blob/main/schedule_your_workflow/describe_schedule_dacx.py) in the context of the rest of the application code.

:::

```python
# ...
async def main():
    client = await Client.connect("localhost:7233")
    handle = client.get_schedule_handle(
        "workflow-schedule-id",
    )

    desc = await handle.describe()

    print(f"Returns the note: {desc.schedule.state.note}")
```

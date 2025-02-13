---
id: how-to-set-a-dynamic-signal-in-python
title: How to set a Dynamic Signal
sidebar_label: Set a Dynamic Signal
description: Use `dynamic=True` on the `@workflow.signal` decorator to make a Signal dynamic.
tags:
- dynamic signal
- python sdk
- code sample
---

<!-- DO NOT EDIT THIS FILE DIRECTLY.
THIS FILE IS GENERATED from https://github.com/temporalio/documentation-samples-python/blob/main/dynamic_handlers/your_dynamic_signal_dacx.py. -->

A Dynamic Signal in Temporal is a Signal that is invoked dynamically at runtime if no other Signal with the same input is registered.
A Signal can be made dynamic by adding `dynamic=True` to the `@signal.defn` decorator.

The Signal Handler should accept `self`, a string input, and a `Sequence[temporalio.common.RawValue]`.
The [payload_converter()](https://python.temporal.io/temporalio.workflow.html#payload_converter) function is used to convert a `RawValue` object to the desired type.

:::copycode Sample application code

The following code sample comes from a working and tested sample application.
The code sample might be abridged within the guide to highlight key aspects.
Visit the source repository to [view the source code](https://github.com/temporalio/documentation-samples-python/blob/main/dynamic_handlers/your_dynamic_signal_dacx.py) in the context of the rest of the application code.

:::

```python
# ...
    @workflow.signal(dynamic=True)
    async def dynamic_signal(self, name: str, args: Sequence[RawValue]) -> None:
        await self._pending_greetings.put(name)
```

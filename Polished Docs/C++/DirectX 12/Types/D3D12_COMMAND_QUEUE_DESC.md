# D3D12_COMMAND_QUEUE_DESC

This structure describes a command queue, which is used to submit command lists to the GPU. It is used when creating a command queue with `ID3D12Device::CreateCommandQueue`.

## Structure Members

| Field      | Description                               |
|------------|-------------------------------------------|
| `Type`     | The type of commands the queue can execute. |
| `Priority` | The scheduling priority of the queue.      |
| `Flags`    | Special behavior flags for the queue.     |
| `NodeMask` | Identifies the target GPU in a multi-adapter setup. |


## `Type`: Command List Type

This field specifies the engine or domain the command queue will execute commands on.

| Type                | Graphics | Compute | Copy    | Typical Use Case        |
|---------------------|:--------:|:-------:|:-------:|-------------------------|
| `D3D12_COMMAND_LIST_TYPE_DIRECT`  | Yes      | Yes     | Yes     | Main rendering and compute queue. |
| `D3D12_COMMAND_LIST_TYPE_COMPUTE` | No       | Yes     | Limited | Asynchronous compute tasks. |
| `D3D12_COMMAND_LIST_TYPE_COPY`    | No       | No      | Yes     | Resource uploading and streaming. |
| `D3D12_COMMAND_LIST_TYPE_BUNDLE`  | N/A      | N/A     | N/A     | Not valid for command queue creation. |

---

## `Priority`: Scheduling Priority

Defines the execution priority of the command queue relative to other queues on the system.

| Priority                          | Behavior                                     | Notes                                       |
|-----------------------------------|----------------------------------------------|---------------------------------------------|
| `D3D12_COMMAND_QUEUE_PRIORITY_NORMAL` | Default scheduling priority.                 | Recommended for most use cases.             |
| `D3D12_COMMAND_QUEUE_PRIORITY_HIGH`   | Gives the queue higher priority.             | Use sparingly to avoid starving other queues. |
| `D3D12_COMMAND_QUEUE_PRIORITY_GLOBAL_REALTIME` | System-level realtime priority. | **Use with caution.** Can disrupt OS rendering and responsiveness. Requires admin privileges. |

---

## `Flags`: Queue Behavior Flags

Specifies special behaviors for the command queue.

| Flag                                | Effect                                                              | When to Use                                    |
|-------------------------------------|---------------------------------------------------------------------|------------------------------------------------|
| `D3D12_COMMAND_QUEUE_FLAG_NONE`     | Default behavior.                                                   | The standard choice for all normal operations. |
| `D3D12_COMMAND_QUEUE_FLAG_DISABLE_GPU_TIMEOUT` | Prevents the GPU from timing out and resetting (TDR). | **Debugging only.** Useful for long-running compute tasks that would otherwise be terminated by the OS. Not for realtime rendering. |

---

## `NodeMask`: Multi-Adapter Node Selection

A bitmask used to specify which GPU node(s) the command queue will target in a multi-adapter system.

| Value   | Meaning                                           |
|---------|---------------------------------------------------|
| `0`     | Targets the default single GPU setup.             |
| Bitmask | Each bit corresponds to a GPU adapter (e.g., `1` for GPU 0, `2` for GPU 1). |

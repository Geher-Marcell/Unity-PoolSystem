# Unity Pool System

Are you having performance issues with your game? Most of the times it's caused by `instantiating` and `destroying` gameobjects every frame.
This project helps to fix these problems by `creating the gameobjects you want to use beforehand` and `reusing them`. 
With this you can save a lot of processing time on the CPU and getting higher FPS in your game.

### Features
- Creating a pool of any gameobject during runtime
- Reducing the poolsize back to it's original after a period of time
- The reducing process is done in multiple frames so the game doesn't stutter

### How to use
- In the inspector
  - Create a gameobject and attach the `PoolManager.cs` script.
  - In the inspector window you can set the `cullInterval` to cull the pool every few seconds (default is 10 seconds).
- From code:
  - You can initialize a pool by calling `PoolManager.Instance.CreatePool()`
    - `name`: The name of the pool.
    - `prefab`: The gameobject you want to pool
    - `size`: The default size of the pool
  - You can retrieve objects by calling `PoolManager.Instance.Getobject()`
    - Either `name` or `index`
  - You can send back on object to the pool `PoolManager.Instance.ReturnObject()`
    - `obj`: The gameobject you want to return to the pool
  - You can also increase the size of the pool temporarly by `Poolmanager.Instance.AddObjectToPool()`
    - Either `name` or `index`

### Planning to add in the future
- Dynamically increasing the size of the pool incase you run out of objects to use
- Keeping track of each object's inactive time and culling based off that

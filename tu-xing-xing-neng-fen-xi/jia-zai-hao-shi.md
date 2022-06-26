# 加载耗时

### 一.概览

c++：在c++层面，线程被平等对待（《C++标准库（第二版）》 946页）

Android：有主线程概念，负责每秒60帧绘制界面，也叫界面线程，加载放在其他线程里，设置合理的[线程优先级](https://developer.android.com/topic/performance/threads#priority)，那么就不会阻塞主线程

### 二.Unity官方回答

Q：请问AssetBundle.LoadAssetAsync()这个真的是异步获取资源吗，我用的个人版unity,这个api会阻塞主线程的，是不是得专业版才行

A：AssetBundle.LoadAssetAsync在加载资源的时候，比如一个Prefab，Prefab里面用到的各种Texture，Mesh，Shader都会在子线程Worker线程进行加载，但是加载完成后会有后处理，比如Shader.Parse是一定会在主线程处理的，纹理和Mesh需要上传到GPU，如果开了多线程渲染并使用AUP功能，非RW的纹理和Mesh的上传会在渲染线程处理，如果没开多线程渲染，那么这一部分还是会由主线程来完成的，这些后处理的名字叫XXX.AwakeFromLoad，如Texture.AwakeFromLoad，当主线程触发这些回调的时候，主线程其他的Update操作就必须等这些后处理完成才能继续。\
还有其他的像Prefab的序列化，各种Component的序列化等也都是在主线程完成的。所以一次AssetBundle.LoadAssetAsync操作，其实并不是完全的异步，主线程中依然是要做不少工作的。具体细节可以观看UWA Day2019年的视频，里面的讲解非常清晰。[https://edu.uwa4d.com/course-intro/1/91?purchased=true](https://edu.uwa4d.com/course-intro/1/91?purchased=true)

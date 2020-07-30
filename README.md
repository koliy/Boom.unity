Simple destruction effect for Unity
==================================

[Demo](https://gfycat.com/CheapWildIcelandichorse)

I had a silly idea of how you could do a destruction effect in Unity, and this
is the result. The idea is to generate a Voronoi diagram for the wall, apply a
few rounds of Lloyd relaxation, and then generate meshes from the cells which
becomes the "shards" of the wall. UV coordinates are also assigned to the front
faces of the shards to make up a continuous texture, but that part could be much
improved. The shards are created in Start() and are all kinematic Rigidbodies.

When you "shoot", a raycast is sent to the backwall which is the origin of the
explosion, and all the shards touching the explosion radius become non-kinematic
and has an explosion force applied to them. 

There are many optimizations one might do for this, but the frame-rate holds up
even on my ancient MacBook Pro. Since this was just a quick project, I didn't
clean up the code too much and haven't made extensive comments, but would be
happy to do so if requested. 

To generate the Voronoi diagram I use the [this library for
c#](https://github.com/PouletFrit/csDelaunay), as experience have taught me that
reimplementing Fortune's algorithm is no fun :)

我对如何在Unity中制造破坏效果有一个愚蠢的想法，这就是结果。我们的想法是为墙壁生成一个Voronoi图，应用几轮Lloyd放松，然后从细胞生成网格，这些网格成为墙壁的“碎片”。UV坐标也被分配到碎片的正面以组成一个连续的纹理，但是这部分可以得到很大的改进。在Start()中创建的碎片都是运动学刚体。



当你“射击”时，射线投射到爆炸的来源后壁，所有接触爆炸半径的碎片都变成非运动学的，并施加爆炸力。



有很多优化可以做到这一点，但帧率即使在我的老MacBook Pro上也能保持。因为这只是一个快速的项目，所以我没有清理太多代码，也没有做大量的注释，但是如果需要的话，我很乐意这样做。



为了生成Voronoi图，我使用了c#的这个库，因为经验告诉我，重新实现Fortune的算法一点也不好玩:)

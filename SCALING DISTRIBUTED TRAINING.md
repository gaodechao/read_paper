###### SCALING DISTRIBUTED TRAINING WITH ADAPTIVE SUMMATION 

MLSys Conference

<b>abstract</b>

* 解决模型更新过程中计算节点之间的通讯瓶颈，从业者使用梯度压缩技术，如稀疏化、量化、低秩更新等。这些技术通常需要选择一个静态压缩比，通常需要用户在模型精度和每次迭代加速之间进行权衡。
* 由于选择高压缩比而导致的性能退化不是根本的，自适应压缩策略可以在保持最终测试精度的同时减少通信。
* 其中小的梯度误差会对模型性能产生不可恢复的影响。我们提出了ACCORDION一种简单而有效的自适应压缩算法
* 虽然ACCORDION平均保持了足够高的压缩率，但它避免了有害的影响，因为在关键的学习机制中，它没有过多地压缩梯度，这是由一个简单的基于梯度规范的准则检测到的。

<b>Introduction</b>

之前的工作有两个方法减少瓶颈：

* 增加batch大小。这样，梯度是由每个worker在一个大的批上计算的，从而减少每个epoch通信的频率
* 梯度压缩技术。以减少通讯数据的大小。这两种方法都需要在性能和准确性之间进行权衡。

使用大的batch可能导致最终精度的退化

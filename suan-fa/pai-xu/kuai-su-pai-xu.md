快速排序（Quick Sort）是一种划分交换排序。它采用一种分治的策略，通常称其为分治法。

分治法的基本思想：将原问题分解为若干个规模更小但结构与原问题相似的子问题。递归地解决这些子问题，然后将这些子问题的解组合为原问题的解。

快速排序的基本思想：

* 分解：在R\[low...high\]中任选一个记录作为基准（Pivot），以此基准将当前无序区划分为左、右两个较小的子区间R\[low...pivotpos-1\]和R\[pivotpos+1...high\],并使左边子区间所有记录的关键词均小于等于基准记录的关键词，右边的子区间中所有记录的关键词均大于等于基准记录的关键词，而基准记录则位于正确的位置上，无须参加后续的排序。
* 求解：通过递归调用快速排序对左、右子区间R\[low...pivotpos-1\]和R\[pivotpos+1...high\]快速排序
* 组合：空操作





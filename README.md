# algorithms_hd_851
- 关于快速排序的非递归实现有以下几个要点：
1. 非递归模拟递归需要栈
2. 栈是保存当前状态用的，保存什么，需要因当前操作需要什么而定，例如遍历树，需要保存的是当前节点的信息。
3. 当知道一个算法的递归实现，要实现非递归，只需要用栈模拟就行了。
4. 接着就是分析递归实现是如何递归的，在递归的地方入栈，在需要用到栈里面的数据的时候出栈即可。

- 下面从递归的代码到非递归代码的角度分析快排递归到非递归的转换：
1. 快速排序递归是在每一次划分之后，继续递归划分左右两边的。
2. 每一次递归需要的就是left和right。
3. 每次划分需要的就是left和right。
4. 所以非递归的时候可以设立一个```Rec```数据结构保存left和right。
5. 在递归的地方将left和right入栈即可。

- 再从快排的算法逻辑角度分析快排非递归的实现思路：
1. 首先，快排是刚开始就进行一次划分。
2. 划分完后会有两个部分，left part和right part。
3. 需要对left part和right part分别进行划分，这就是递归进行（每次递归其实做的事情是同一种事情，只不过参数不一样而已）。
4. 按照以上逻辑，首先设立一个栈数据结构，然后把第一次划分的状态（left，right）保存。
5. 当栈空的时候，也就是所有的划分工作都做完了，就结束递归。
6. 当栈非空的时候，需要将栈里面的数据拿出一个，进行一次划分。
7. 划分完毕，按照上面3的逻辑，需要对left part和right part在进行一次划分，那么就需要将他们的left和right保存进去。
8. left part和right part的left和right就是上一次划分的partitial决定的，分别是[left, partitial - 1]和[partitial + 1, right]
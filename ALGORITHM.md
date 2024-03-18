
# 1.基础
### 【1】98. 验证二叉搜索树
- double和int最大最小值：
>     double minDouble = -Double.MAX_VALUE; // Double.MIN_VALUE是最小的非负正数0.00000000...001
>     double maxDouble = Double.MAX_VALUE;
>     int minInt = Integer.MIN_VALUE; // 整数不存在此类问题

# 2.数组

# 3.字符串 
### 【1】125. 验证回文串 
- 大写小写字符转换：
>     String str = "HELLO WORLD";
>     String lowercaseStr = str.toLowerCase();

- 移除非字母和非数字：
>     String str = "Hello123*** World!!!";
>     String result = str.replaceAll("[^a-zA-Z0-9]",""); // 正则替换非数字非字母
>     String result = str.replaceAll("[\u4e00-\u9fa5]",""); // 替换所有中文
>     boolean isWord = words[i].matches("\\w+"); // 使用正则表达式进行匹配所有单词；\\w：代表一个单词字符，即a-z、A-Z、0-9或下划线_；+：表示前面的字符（在这里是\w）可以出现一次或多次。

### 【2】71. 简化路径 
- string增减操作：
>     StringBuffer strBuffer = new StringBuffer(); // 不安全，比StringBuilder更快速
>     strBuffer.append("end"); // 在后边插入
>     strBuffer.insert(0, "begin"); // 在前边插入

- string预处理操作，分割处理：
>     String[] names = path.split("/"); // 分割path，可以为空


- 字符串数组互转：
>     char[] chars = str.toCharArray();
>     String str = chars.toString();
>     char i = str.charAt(0); // 获取str中第0个字符

# 4.树
- BFS广度优先层次遍历：
>     public void bfs(TreeNode root) {
>         if(root==null) {
>             return null;
>         }
>         LinkedList<TreeNode> queue = new LinkedList<TreeNode>();
>         queue.add(root); // 从头加入
>         while(!queue.isEmpty()) {
>             TreeNode tmp = queue.poll(); // 从头取出
>             if(tmp.left!=null) {
>                 queue.add(tmp.left);
>             }
>             if(tmp.right!=null) {
>                 queue.add(tmp.right);
>             }
>         }
>         //返回处理完的根节点
>         return void;
>     }

- BFS先序遍历：
>     Deque<TreeNode> queue = new LinkedList<TreeNode>();
>     TreeNode p = root;
>     while(p != null || !queue.isEmpty()) {
>         if (p != null) { // while (p != null) 可无continue
>             // 先序遍历
>             queue.push(p); // 从尾加入
>             p = p.left;
>             continue;
>         }
>         p = queue.pop(); // 从尾出队
>         p = p.right;
>     }


- DFS深度优先遍历：
>     public void dfs(TreeNode root) {
>         if (root == null) {
>           return;
>         }
>         // 代码在此处表示前序
>         dfs(root.left);
>         // 代码在此处表示中序
>         dfs(root.right);
>     }

# 5.链表
### 【2】92. 反转链表 II
- 反转链表：
>     public void dfs(TreeNode root) {
>         if (root == null) {
>           return;
>         }
>         // 代码在此处表示前序
>         dfs(root.left);
>         // 代码在此处表示中序
>         dfs(root.right);
>     }
ListNode pre = preNode.next;
        ListNode tailNode = pre.next;
        while (index < right && pre.next != null) {
            ListNode current = tailNode;
            tailNode = tailNode.next;
            current.next = pre;
            pre = current;
            index++;
        }
# x.基本结构
### 【1】20. 有效的括号
- 栈的使用：
>     Stack<Character> stack = new Stack<>(); // 两种初始化方式
>     stack.isEmpty(); // = stack.size() == 0
>     stack.push(aChar);
>     stack.pop();
>     stack.peek(); // 获取栈顶

- 哈希映射HashMap的使用：
>     Map<Character, Character> pairs = new HashMap<Character, Character>() {{
>         put(')', '('); // 初始化
>     }};

### 【1】199. 二叉树的右视图
- 队列的使用：
>     // 双端队列
>     Deque<Character> que = new LinkedList<Character>();
>     que.add('t'); // 添加到队列尾部
>     que.offer('t'); // 添加到队列尾部，比add更好
>     que.peek(); // 查看头部元素不出队列，为空返回null
>     que.remove; // 获取头部元素并删除元素, 为空报错
>     que.poll(); // 获取头部元素并出队列，为空返回null，比remove好
>     // 单端队列
>     Queue
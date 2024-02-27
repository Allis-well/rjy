
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



- 字符串数组互转：
>     char[] chars = str.toCharArray();
>     String str = chars.toString();

# 4.遍历树
- BFS广度优先：
>     public void bfs(TreeNode root) {
>         if(root==null) {
>             return null;
>         }
>         LinkedList<TreeNode> queue = new LinkedList<TreeNode>();
>         queue.add(root); // 加入头
>         // while (p || !queue.isEmpty()) { // 先序遍历，p不为空或栈不为空一直向左子到底
>         while(!queue.isEmpty()) { // 中序遍历不为空
>             TreeNode tmp = queue.poll();
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

- DFS深度优先：
>     public void dfs(TreeNode root) {
>         if (root == null) {
>           return;
>         }
>         // 代码在此处表示前序
>         dfs(root.left);
>         // 代码在此处表示中序
>         dfs(root.right);
>     }


# 3.基本结构
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
>     Deque<Character> que = new LinkedList<Character>();
>     que.add('t');
>     que.offer('t');添加到队列尾部，比add更好
>     que.peek(); // 获取头部元素不删除，为空返回null
>     que.poll(); // 获取头部元素并删除元素，为空返回null
>     que.remove; // 获取头部元素并删除元素, 为空报错
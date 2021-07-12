# Python 基本題

1. append( ) 與extend( ) 的差異

    append( ) 會將List 視為一個元素加入原本的List

    ```python
    a = ["a", "b", "c"]
    b = [1, 2, 3]
    a.append(b)
    print(a) # ['a', 'b', 'c', [1, 2, 3]]

    ```

    extend 會拆散第二個list 在合併回原本的list

    ```python
    a = ["a", "b", "c"]
    b = [1, 2, 3]
    a.extend(b)
    print(a) # ['a', 'b', 'c', 1, 2, 3]
    ```

2. sort( ) 與 sorted ( )的差別

    sort( ) 沒有回傳值 會改變原本內容

    sorted () 有回傳值 回傳排序後的內容 不改變原本的

    ```python
    string_list = ['abc', 'ab', 'linda', 'a']
    new_str = sorted(string, key = lambda x:len(x))

    print(string_list)  # ['abc', 'ab', 'linda', 'a']
    print(new_str) # ['a', 'ab', 'abc', 'linda']

    string_list.sort(key=len)
    print(string) # ['a', 'ab', 'abc', 'linda']
    ```

3. 什麼是生成器
    1. 將cities = ['A city', 'B city']和populations = [100, 200] 打包該怎麼做

        使用zip 可轉成tuple

        ```python
        cities = ['A city', 'B city']
        populations = [100, 200]
        for i in zip(cities,populations):
            print(i)
        # ('A city', 100)
        # ('B city', 200)
        ```

        或是在將zip 物件轉成list 或是dic

        ```python
        cities = ['A city', 'B city']
        populations = [100, 200]
        result = list(zip(cities,populations)) 
        print(result) # [('A city', 100), ('B city', 200)]
        
        result2 = dict(zip(cities,populations))
        print(result2) # {'A city': 100, 'B city': 200}
        ```

    可以返回一組可迭代項目的函數

    ```python
    num = 10
    square = [n ** 2 for n in range(1,num +1)]
    print(square)
    ```

4. 合併 兩個fruits dic 若有重複的值 由後面的值取代

    用list.update( )

    ```python
    fruits1 = {'Apple': 50, 'Orange':30,}
    fruits2 = {'Orange':40,'Banana':60}
    fruits1.update(fruits2)
    print(fruits1) # {'Apple': 50, 'Orange': 40, 'Banana': 60}
    ```

5.  將 str1 = ['a', 1] 和 str2 = ['b', 2] 處理成 {'a':1, 'b', 2 }的 dict

    ```python
    str1 = ['a', 1]
    str2 = ['b', 2]
    x = dict([str1,str2])
    print(x)
    ```

6. 用生成式 產生差為11的等差數列

    ```python
    print([i*11 for i in range(10)])
    # [0, 11, 22, 33, 44, 55, 66, 77, 88, 99]
    ```

7. 有三個國家不同公司的資料如何去除重複的公司

    ```python
    asia = ['IBM', 'Google', 'Acer', 'Asus', 'TSMC']
    euro = ['Philip', 'HP', 'Simens', 'IBM', 'Google']
    america = ['HP', 'Microsoft', 'Google', 'IBM']
    ```

    使用set ( )  可以去除list當中重複的元素

    ```python
    customers = asia + euro + america
    cust = set(customers)
    customer = list(cust)
    print(customer) 
    ```

    ['Simens', 'Asus', 'Acer', 'Google', 'Philip', 'IBM', 'Microsoft', 'HP', 'TSMC']

    set 的其他用法

    ```python
    vowels = set('aeiou') # {'o', 'u', 'i', 'e', 'a'}
    letters = set('alice') # {'c', 'i', 'l', 'e', 'a'}
    subnet = set('ae') # {'a','e'}
    ```

    取交集

    ```python
    vowels & letters  #{'a', 'e', 'i'}
    ```

    取聯集

    ```python
    vowels | letters # {'c', 'o', 'u', 'i', 'l', 'e', 'a'}
    ```

    取差集

    ```python
    vowels - letters # {'o', 'u'}
    ```

    取對稱差集 (聯集減去交集)

    ```python
    vowels ^ letters  # {'c', 'l', 'o', 'u'}
    # 相等於
    (letters | vowels) - (letters & vowels)
    ```

    檢查是否為子集

    ```python
    # {'a','e'} 是否為 {'c', 'i', 'l', 'e', 'a'} 的子集
    subnet <= letters # True
    # 相等於
    subnet.issubset(letter) 

    # {'c', 'i', 'l', 'e', 'a'} 是否為 {'a','e'} 的子集
    subnet >= letters # False
    ```

    檢查是否為超(父)集

    ```python
    #{'c', 'i', 'l', 'e', 'a'} 是否完全包含 {'a','e'} 
    letters.issuperset(subnet) # True
    ```

8. 有兩個list 如何找出有交集的

    ```python
    list1 = [1, 2, 3, 4, 5]
    list2 = [3, 4, 5, 6, 7]
    x = [i for i in list1 if i in list2]
    print(x) # [3, 4, 5]
    ```

9. 如何打亂一副鋪克牌 與 隨機選出n張牌

    ```python
    import random
    porker = ['A', '1', '2', '3', '4', '5', '6', '7',
              '8', '9', '10', 'J', 'Q', 'K']
    random.shuffle(porker)
    print(porker)
    # ['K', '2', '10', '4', '1', 'A', 'J', '9', '3', '8', '7', '5', 'Q', '6']
    ```

    亂數選出

    ```python
    import random
    n = 5
    porker = ['A', '1', '2', '3', '4', '5', '6', '7',
              '8', '9', '10', 'J', 'Q', 'K']
    result = random.sample(porker,n)
    print(result)
    ```

10.  將一串 [4, 2, 5, 3, 1] 做 小到大 與 大到小排序

     ```python
        x = [4, 2, 5, 3, 1]
        x.sort()
        print(x) # [1, 2, 3, 4, 5]

        x = [4, 2, 5, 3, 1]
        x.sort(reverse=True)
        print(x) # [5, 4, 3, 2, 1]
     ```

11.  lambda 是什麼

        是python 中的匿名函式，寫法為 lambda: 輸入參數: 函式內容

        ex 計算平方  


        ```python
        square = lambda x: x * x
        print(square(10)) # 100
        ```

12. 將  {'a':24,'g':52,'i':12,'k':33} 依照key 排序 與 依照value排

    用dic.items() 會將dict的結果轉為包著tuple的list

    ```python
    a = {'a':24,'g':52,'i':12,'k':33}
    b = sorted(a.items(),key=lambda x: x[0]) #照key
    print(b) 
    # [('a', 24), ('g', 52), ('i', 12), ('k', 33)]

    b = sorted(a.items(),key=lambda x: x[1]) #照value
    print(b)
    # [('i', 12), ('a', 24), ('k', 33), ('g', 52)]
    ```

    若一個dict 直接丟入sort會只拿到key or value的排序

    ```python
    a = {'a':24,'g':52,'i':12,'k':33}
    b = sorted(a,key=lambda x: x[0]) #照key
    print(b)
    #['a', 'g', 'i', 'k']
    ```

13. 请按list中元素的age 由大到小排序

    ```python
    alist = [{'name':'a','age':20},{'name':'b','age':30},{'name':'c','age':25}]

    result = sorted(alist,key=lambda x:x['age'],reverse=True)
    print(result)
    # [{'name': 'b', 'age': 30}, {'name': 'c', 'age': 25}, {'name': 'a', 'age': 20}]
    ```

14. 使用sorted 將 [-8, 5, 9, -2, -11, 12, 1, 10, -5] 正值的有小到大排序 負值的由大到小排序

    ```python
    lst = [-8, 5, 9, -2, -11, 12, 1, 10, -5]
    ans = sorted(lst,key=lambda x: (x<0, abs(x)))
    print(ans)
    #[1, 5, 9, 10, 12, -2, -5, -8, -11]
    ```

    解說

     abs() 是轉為絕對值的正數 在，lambda丟出的是tuple

    ```python
    (True, 8)
    (False, 5)
    (False, 9)
    (True, 2)
    (True, 11)
    (False, 12)
    (False, 1)
    (False, 10)
    (True, 5)
    ```

    key就是排序關鍵字，默認是list裡的元素本身

    比如比較1和10的大小的時候，就是看1<10的結果，True的話1在前，False的話10在前。
    而如果你給了**它一個函數作為key**，那麼比較1和10的時候

    就會看key(1)<key(10)的結果，而不是1<10。
    所以根據你的key，你的sort函數作比較的時候，實際比較的是你的key生成出來的結果，也就是那個tuple。

    比較tuple的方式，是按照裡面元素的順序一個一個比，找到第一個不相等的元素，這個元素的比較結果就是tuple的比較結果。

    所以當一個正數和一個負數比較的時候

    是(False, xxx) vs (True, yyy)，那麼第一個元素就不相等了，False比較小，所以正數在前面。

    如果符號相同，那麼tuple裡的第一個元素就是相等的，那麼就比較第二個元素，也就是絕對值小的在前面了。

15. 有個姓名與年齡組成的list 

    ```python
    member = [['Peter', 25],
              ['Mary', 22],
              ['Kevin', 29],
              ['Jessica', 22],
              ['Nancy', 22],
              ['Tom', 18]]
    ```

    要依照姓名由小到大排序，依照年齡由大到小排序

    ```python
    #姓名由小到大
    ans = sorted(member,key=lambda x:x[0])
    print(ans)
    # [['Jessica', 22], ['Kevin', 29], ['Mary', 22], ['Nancy', 22], ['Peter', 25], ['Tom', 18]]

    #年齡由大到小
    ans = sorted(member,key=lambda x:x[1],reverse=True)
    print(ans)
    #[['Kevin', 29], ['Peter', 25], ['Mary', 22], ['Jessica', 22], ['Nancy', 22], ['Tom', 18]]
    ```

16. 有一字典內容為

    ```python
    member = {'Peter':25,
              'Kevin':29,
              'Tom':18}
    ```

    1.  字典轉成串列, 元素是元組 
    2. 依鍵值由小到大排序
    3. 轉為字典

    ```python
    member_zip = zip(member.keys(),member.values()) # 單純zip物件只能印出位置

    member_list = [i for i in member_zip]
    print(member_list)  # [('Peter', 25), ('Kevin', 29), ('Tom', 18)]

    member_sort = sorted(member_list,key=lambda x: x[0])
    print(member_sort)  # [('Kevin', 29), ('Peter', 25), ('Tom', 18)]

    dict = {k:v for k,v in member_sort}
    print(dict)  # {'Kevin': 29, 'Peter': 25, 'Tom': 18}
    ```

17.  有一串列為['a', 'b', 'c'] 請將元素設為字典的key 隨機建立1~10的value 

     ```python 
        import random
        lst = ['a', 'b', 'c']
        ans = {i:random.randint(1,10) for i in lst}
        print(ans)
        # {'a': 2, 'b': 9, 'c': 3}
     ```

18. 說明內建函數 map ( ) 怎麼使用，並用程式說明

    map ( function, iterable )
    將可迭代的物件依序放入function中，將function的結果回傳，常用lambda表達式

    例如輸出list元素的平方

    ```python
    numbers = [1,2,3,4,5]
    square = list(map(lambda x: x**2, numbers)) # 單純map物件只能印出位置
    print(square) # [1, 4, 9, 16, 25]

    # 做法2 [i**2 for i in numbers ] 
    ```

19.  請說明*args 與 **kwargs 的差別

        *args : 是指函數可以有任意數量的參數，本質是tuple
        **kwargs 是指函數可以有任意數量的關鍵字參數，本質是dict


        ```python
            def fun(*args, **kwargs):
                print('args =', args) 
                    # args = (1, 2, 3, 4, 5)

                print('kwargs =', kwargs) 
                    # kwargs = {'A': 'I', 'B': 'like', 'C': 'Python'}

            fun(1, 2, 3, 4, 5, A='I', B='like', C='Python')
        ```

20. 利用Nested function 計算兩座標點的距離

    ```python
    def dist(x1,y1,x2,y2):          # 計算2點之距離函數
        def mySqrt(z):              # 計算開根號值
            return z ** 0.5
        dx = (x1 - x2) ** 2
        dy = (y1 - y2) ** 2
        return mySqrt(dx+dy)

    print(dist(0,0,1,1)) # 1.4142135623730951
    ```

21. 在不用sort()的方法下設計一函數將list排序

    ```python
    def rtn_min(lst):
        min_ = min(lst)
        sort_lst.append(min_)
        lst.remove(min_)
        if lst:
            rtn_min(lst)
        return sort_lst

    sort_lst = []
    data = [1, 7, 3, 9, 2]
    print(rtn_min(data))
    # [1, 2, 3, 7, 9]
    ```

22. 請解釋甚麼是閉包 closure

    有個內部函數可以拿到外面的值，而此函數中存在自己才能取用的變數，外界無法得知。

    ```python
    def outer():
        b = 10                  # inner所使用的變數值
        def inner(x):
            return 5 * x + b    # 引用第3行的b
        return inner

    b = 2
    f = outer() # 將整個inner function 傳給f 
    # 此時inner function 的b 已經是 outer 裡面的b=10 
    print(f(b)) # 再傳入inner 要的 x 
    # 20
    ```

23. 費式數列輸入n 回傳index = n 的值

    ```python
    def fabo(n):
        if n == 0 or n == 1:
            return 1
        else:
            return fabo(n-1) + fabo(n-2)

    print(fabo(4)) #５
    ```

24. 計算1~10的加總

    ```python
    sum(range(1,11))
    ```

25. 輸入一個數字 ex 112 將尾數都轉為0

    ```python
    input = 112
    tmp_num = int(input/10) * 10
    print(tmp_num) # 110
    ```

26. 計算 等差數列 的合，ex 起始為1 終點值為10 間隔為3

    公式 (首項+末項) * 項數 / 2

    ```python
    # 使用loop
    print(sum(range(1, 10+1 ,3))) # 22

    # 不使用loop
    d = (int(10-1) / 3) + 1 # 4
    ans = (10+1) * d / 2 
    print(ans) # 22
    ```

27. 將一字串 排除重複且重新排列大小

    ```python
    strings = 'ajkadcbkkkzzzxiuuuii'

    tmpStrs = set(strings)
    print(tmpStrs)  #會是dict {'d', 'j', 'b', 'x', 'i', 'a', 'k', 'u', 'z', 'c'}
    ans = sorted(tmpStrs) 
    print(ans)  #會是list ['a', 'b', 'c', 'd', 'i', 'j', 'k', 'u', 'x', 'z']
    ```

28. 畫出等腰三角形

    ```python
    def fig(h):
        for i in range(h):
            print(' '*(h-i-1)+'*'*(2*i+1))
    fig(3)
    ```

    ```python
    	*
     ***
    *****
    ```

29. 畫出正直角三角形 與 倒直角三角形

    ```python
    n = 3
    for i in range(1,n+1):
        print('*' * i)

    *
    **
    ***
    ```

    倒三角

    ```python
    for i in range(n,0,-1):
    		print('*' * i)

    ***
    **
    *
    ```

30. 字串 '''FBI Mark told CIA Linda that the secret USB had given to FBI Peter''' 

    計算 FBI出現幾次，用xxx換置FBI

    ```python
    msg = '''FBI Mark told CIA Linda that the secret USB had given to FBI Peter'''
    print(msg.count('FBI')) # 2
    msg = msg.replace('FBI','xxx')
    print(msg)
    # xxx Mark told CIA Linda that the secret USB had given to xxx Peter
    ```

31.  檢查文字是否為 http 開頭
     ```python
     str.startswith(str, beg=0,end=len(string));
     ```

     ```python
        site = "http://abc.123"
        if site.startswith("http://") or site.startswith("https://"):
            print("網址格式正確")
        else:
            print("網址格式錯誤")
     ```

32. 檢查文字是否為 wow結尾

    str.endswith(suffix[, start[, end]])

    ```python
    str = "this is string example....wow!!!";
    suffix = "wow!!!";
    print(str.endswith(suffix)) # True
    ```

33. 排列出 兩個數字list的所有組合

    ```python
    n1 = [1,2,3]
    n2 = [1,2,3]
    result = [[x, y] for x in n1 for y in n2] # 先固定 x 再去跑y的迴圈
    print(result)
    # [1, 1], [1, 2], [1, 3], [2, 1], [2, 2], [2, 3], [3, 1], [3, 2], [3, 3]]
    ```

34.  將顏色與形狀的list 排列組合

     ```python
        colors = ["Red", "Green", "Blue"]
        shapes = ["Circle", "Square"]
        result = [[color, shape] for color in colors for shape in shapes]
        print(result)
        #[['Red', 'Circle'], ['Red', 'Square'], ['Green', 'Circle'], ['Green', 'Square'], ['Blue', 'Circle'], ['Blue', 'Square']]
     ```

35. 寫出一個計算最大公因數的function

    ex a = 15, b = 6

    ```python
    def gcd(a,b):
    		while b != 0: 
    				tmp = a % b # 相除的餘數當作下次的除數(b) 
    				a = b
    				b = a
    		return a  # 3
    ```

    用遞迴寫同樣的功能

36. 計算最小公倍數

    ```python
    def gcp(a,b):
    	return a if b == 0 else gcd(b, a % b)
    ```

    ex a = 15 , b = 6

    兩數相乘 / 最大公因數

    ```python
    def gcd(a, b):
        while b != 0:
            tmp = a % b
            a = b
            b = tmp
        return a
    
    def lcm(a,b):
        return a * b // gcd(a,b)
    
    print(lcm(a,b)) # 30
    ```

37. 取出一list中出現最多的元素
    ```python
    nums = [2,2,1,1,3,2,2]
    max_item = max(nums, key=nums.count)
    print(max_item) # 2
    ```

38. 將list透過出現次數排序
    ```python
    from collections import Counter
    nums = [2,2,1,1,3,2,2]

    # print(Counter(nums).get(1))  # 2
    # print(Counter(nums).get(2))  # 4

    nums.sort(key=Counter(nums).get)
    print(nums)  # [3, 1, 1, 2, 2, 2, 2]
    ```

39. 使用 xor 找出list 中單獨的數字 nums = [4,1,2,1,2] 
    xor 規則

    ```python
    0 xor 0 = 0
    0 xor 1 = 1
    1 xor 0 = 1
    1 xor 1 = 0
    ```

    1. xor 符合交換律 **a^b == b^a**

    2. 0^a 是 a

    3. a^a 是 0

    解題方式

    ```python
    length = len(nums)
    r =nums[0]
    for i in range(1, length):
        r = r ^ nums[i] 
    print(r) # 4
    ```
    因符合交換率可拆解成  4 ^ (1 ^ 1) ^ (2 ^ 2) => 4 ^ 0 ^ 0  ⇒ 4
    
    每一輪的更新步驟
    ```python
    r = 4 ( 0b100 ) itme =  1 ( 0b1 )
    after xor =  5 bin =  0b101

    r = 5 ( 0b101 ) itme =  2 ( 0b10 )
    after xor =  7 bin =  0b111

    r = 7 ( 0b111 ) itme =  1 ( 0b1 )
    after xor =  6 bin =  0b110

    r = 6 ( 0b110 ) itme =  2 ( 0b10 )
    after xor =  4 bin =  0b100
    ```

40. 反轉linked list ex [1,2,3,4,5]
    ![image](/images/206.rev1ex1.jpg)

    ```python
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next
    class Solution:
        def reverseList(self, head: ListNode) -> ListNode:
            reverse = None
            
            while head:
                next_node = head.next
                head.next = reverse
                reverse = head
                head = next_node
            return reverse
    ```
41. 變更list中部分元素的值 test = [0,1,2,3,4,5,6,7,8,9,10] 將 2,4,6,8,10的元素，換成"x"字串
    
    先切出list中要更換的元素，創建另一個list 放入要替換的元素，兩者list長度相等才能賦值
    ```python
    test = [0,1,2,3,4,5,6,7,8,9,10]
    print(test[2:11:2]) # [4, 6, 8, 10]
    test[2:11:2] = ['x'] * 5
    print(test) # [0, 1, 2, 3, 'x', 5, 'x', 7, 'x', 9, 'x']
    ```
42. 計算一個字串中每個字元出現的次數，按照字元出現順序 ex s="apple"
    ```python
    s_count_pair = [(i, s.count(i)) for i in s ]
    print(s_count_pair ) # [('a', 1), ('p', 2), ('p', 2), ('l', 1), ('e', 1)]
    ```
    或者使用Count 透過取index的方式拿到出現次數

    ```python
    from collections import Counter

    s_count = Counter(s)
    s_count_pair = [(i, s_count[i]) for i in s]
    print(s_count_pair) # [('a', 1), ('p', 2), ('p', 2), ('l', 1), ('e', 1)]
    ```
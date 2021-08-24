## 第一部分 基础知识

### 第一章 起步

安装Anaconda

官网：https://www.anaconda.com/

### 第二章 变量和简单数据类型


```python
#2-1
a = 'hello,world'
print(a)
```

    hello,world
    


```python
#2-2
b = 'hello,world'
print(b)
b = 'hello,python'
print(b)
```

    hello,world
    hello,python
    


```python
#2-3
c = 'Frank'
print('hello '+c+'! How are you?')
```

    hello Frank! How are you?
    


```python
#2-4
d = 'Alex'
print(d.upper())
print(d.lower())
print(d.title())
```

    ALEX
    alex
    Alex
    


```python
#2-5
e = 'Einstein'
f = '"A person who never made a mistake never tried anything new."'
print(e+' once said,'+f)
```

    Einstein once said,"A person who never made a mistake never tried anything new."
    


```python
#2-6
e = 'Einstein'
f = '"A person who never made a mistake never tried anything new."'
print(e+' once said,'+f)
```

    Einstein once said,"A person who never made a mistake never tried anything new."
    


```python
#2-7
g = '\n\tBob\t\n\n'
print('1 '+g)
print('2 '+g.strip())
print('3 '+g.rstrip())
print('4 '+g.lstrip())
```

    1 
    	Bob	
    
    
    2 Bob
    3 
    	Bob
    4 Bob	
    
    
    


```python
#2-8
print(1+7)
print(2*4)
print(11-3)
print(40//5)
```

    8
    8
    8
    8
    


```python
#2-9
h = 7
print('My favourite number is '+str(h)+'.')
```

    My favourite number is 7.
    


```python
#2-10
i = 'love'
# 将字符串‘love’赋值给变量i
```


```python
#2-11
import this
```

    The Zen of Python, by Tim Peters
    
    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!
    

### 第三章 列表简介


```python
#3-1
names = ['ming','gang','hong','qiang']
print(names[0])
print(names[1])
print(names[2])
print(names[3])
```

    ming
    gang
    hong
    qiang
    


```python
#3-2
names = ['ming','gang','hong','qiang']
print('hi '+names[0])
print('hi '+names[1])
print('hi '+names[2])
print('hi '+names[3])
```

    hi ming
    hi gang
    hi hong
    hi qiang
    


```python
#3-3
trip = ['bicycle', 'motor', 'car']
print('Would you like to own a '+trip[0])
print('Would you like to own a '+trip[1])
print('Would you like to own a '+trip[2])
```

    Would you like to own a bicycle
    Would you like to own a motor
    Would you like to own a car
    


```python
#3-4
guest = ['sun', 'moon', 'star', 'mars']
print('I invited you to dinner,'+ guest[0])
print('I invited you to dinner,'+ guest[1])
print('I invited you to dinner,'+ guest[2])
print('I invited you to dinner,'+ guest[3])
```

    I invited you to dinner,sun
    I invited you to dinner,moon
    I invited you to dinner,star
    I invited you to dinner,mars
    


```python
#3-5
print(guest[3].title()+ ' refused me')
guest[3] = 'water'
print('I invited you to dinner,'+ guest[0])
print('I invited you to dinner,'+ guest[1])
print('I invited you to dinner,'+ guest[2])
print('I invited you to dinner,'+ guest[3])
```

    Mars refused me
    I invited you to dinner,sun
    I invited you to dinner,moon
    I invited you to dinner,star
    I invited you to dinner,water
    


```python
#3-6
print('bigger table')
guest.insert(0,'tree')
guest.insert(2,'falsh')
guest.append('stone')
print('I invited you to dinner,'+ guest[0])
print('I invited you to dinner,'+ guest[1])
print('I invited you to dinner,'+ guest[2])
print('I invited you to dinner,'+ guest[3])
print('I invited you to dinner,'+ guest[4])
print('I invited you to dinner,'+ guest[5])
print('I invited you to dinner,'+ guest[6])
```

    bigger table
    I invited you to dinner,tree
    I invited you to dinner,sun
    I invited you to dinner,falsh
    I invited you to dinner,moon
    I invited you to dinner,star
    I invited you to dinner,water
    I invited you to dinner,stone
    


```python
#3-7
print('table is too late')
a = guest.pop()
print('sorry,'+a)
a = guest.pop()
print('sorry,'+a)
a = guest.pop()
print('sorry,'+a)
a = guest.pop()
print('sorry,'+a)
a = guest.pop()
print('sorry,'+a)
print('come,'+guest[0])
print('come,'+guest[1])
del guest[1]
del guest[0]
print(guest)
```

    table is too late
    sorry,stone
    sorry,water
    sorry,star
    sorry,moon
    sorry,falsh
    come,tree
    come,sun
    []
    


```python
#3-8
travel = ['desert', 'canyon', 'mountain', 'river', 'forest']
print(travel)
print('*'*20)
print(sorted(travel))
print(travel)
print('*'*20)
print(sorted(travel,reverse=True))
print(travel)
print('*'*20)
travel.reverse()
print(travel)
print('*'*20)
travel.reverse()
print(travel)
print('*'*20)
travel.sort()
print(travel)
print('*'*20)
travel.sort(reverse=True)
print(travel)
```

    ['desert', 'canyon', 'mountain', 'river', 'forest']
    ********************
    ['canyon', 'desert', 'forest', 'mountain', 'river']
    ['desert', 'canyon', 'mountain', 'river', 'forest']
    ********************
    ['river', 'mountain', 'forest', 'desert', 'canyon']
    ['desert', 'canyon', 'mountain', 'river', 'forest']
    ********************
    ['forest', 'river', 'mountain', 'canyon', 'desert']
    ********************
    ['desert', 'canyon', 'mountain', 'river', 'forest']
    ********************
    ['canyon', 'desert', 'forest', 'mountain', 'river']
    ********************
    ['river', 'mountain', 'forest', 'desert', 'canyon']
    


```python
#3-9
print('location :'+str(len(travel)))
```

    location :5
    


```python
#3-10
print('略')
```

    略
    


```python
#3-11
print('略')
```

    略
    

### 第四章 操作列表


```python
#4-1
bicycles = ['Trek', 'Merida', 'Giant', 'Canyon']
for i in bicycles:
    print(i)
    print('I like '+i)
print('I really like riding')
```

    Trek
    I like Trek
    Merida
    I like Merida
    Giant
    I like Giant
    Canyon
    I like Canyon
    I really like riding
    


```python
#4-2
animal = ['cat', 'dog', 'pig', 'cow']
for i in animal:
    print(i)
    print(i+' has four legs')
print('all these animals have four legs')
```

    cat
    cat has four legs
    dog
    dog has four legs
    pig
    pig has four legs
    cow
    cow has four legs
    all these animals have four legs
    


```python
#4_3
number = range(1,21)
for i in number:
    print(i)
```

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    


```python
#4-4
print('略')
```

    略
    


```python
#4-5
number = list(range(1,1000001))
max(number),min(number),sum(number)
```




    (1000000, 1, 500000500000)




```python
#4-6
number = range(1,20,2)
for i in number:
    print(i)
```

    1
    3
    5
    7
    9
    11
    13
    15
    17
    19
    


```python
#4-7
number = range(3,30,3)
for i in number:
    print(i)
```

    3
    6
    9
    12
    15
    18
    21
    24
    27
    


```python
#4-8
number = range(1,11)
for i in number:
    print(i**2)
```

    1
    4
    9
    16
    25
    36
    49
    64
    81
    100
    


```python
#4-9
number = [i**3 for i in range(1,11)]
number
```




    [1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]




```python
#4-10
print('The first three items in the list are:')
print(bicycles[0:3])
print('The middle three items in the list are:')
print(bicycles[:3])
print('The last three items in the list are:')
print(bicycles[-3:])
```

    The first three items in the list are:
    ['Trek', 'Merida', 'Giant']
    The middle three items in the list are:
    ['Trek', 'Merida', 'Giant']
    The last three items in the list are:
    ['Merida', 'Giant', 'Canyon']
    


```python
#4-11
bike = bicycles[:]
bicycles.append('S_work')
bike.append('Cervelo')
for i in bicycles:
    print('I like'+i)
for k in bike:
    print('She like'+k)

```

    I likeTrek
    I likeMerida
    I likeGiant
    I likeCanyon
    I likeS_work
    She likeTrek
    She likeMerida
    She likeGiant
    She likeCanyon
    She likeCervelo
    


```python
#4-12
print('略')
```

    略
    


```python
#4-13
food = 'fish', 'meat', 'beef', 'fruit'
for i in food:
    print(i)
food = 'fish', 'pork', 'beef', 'vegatable'
for i in food:
    print(i)
```

    fish
    meat
    beef
    fruit
    fish
    pork
    beef
    vegatable
    


```python
#4-14
print('略')
```

    略
    


```python
#4-15
print('略')
```

    略
    

### 第五章 if语句


```python
#5-1
bike = 'canyon'
print('Is bike canyon?I predict True')
print(bike=='canyon')
```

    Is bike canyon?I predict True
    True
    


```python
#5-2
a = 'ming'
b = 'ming'
c = a.upper()
d = 5
e = 6
f = 7
bike = ['Giant', 'Merida', 'Canyon']
print(a==b,a==c,'Merida' in bike, e>d and e<f)
```

    True False True True
    


```python
#5-3
alien = 'green'
if alien == 'green':
    print('got five')
```

    got five
    


```python
#5-4
alien = 'red'
if alien == 'green':
    print('got five')
else:
    print('lose')
```

    lose
    


```python
#5-5
alien = 'yellow'
if alien == 'green':
    print('got five')
elif alien == 'yellow':
    print('got three')
else:
    print('lose')
```

    got three
    


```python
#5-6
age = 18
if age < 2:
    print('baby')
elif age < 4:
    print('kid')
elif age < 13:
    print('child')
elif age < 20:
    print('teen')
else:
    print('adult')
```

    teen
    


```python
#5-7
fruit = ['apple', 'peach', 'Grapes']
if 'apple' in fruit:
    print('I like apple')
elif 'banana' in fruit:
    print('I like banana')
else:
    print('no my fruit')
```

    I like apple
    


```python
#5-8
users = ['admin', 'ming', 'gang', 'hong']
for i in users:
    if i == 'admin':
        print('Hello boss')
    else:
        print('welcome '+i)
```

    Hello boss
    welcome ming
    welcome gang
    welcome hong
    


```python
#5-9
users = []
if users:
    for i in users:
        if i=='admin':
            print('Hello boss')
        else:
            print('welcome '+i)
else:
    print('no user')
```

    no user
    


```python
#5-10
now_users = ['admin', 'ming', 'gang', 'hong', 'LEE']
current_users = ['feng', 'lin', 'lee', 'gang']
for i in now_users:
    if i.lower() in [k.lower() for k in current_users]:
        print('occupied,change please')
    else:
        print('available')
```

    available
    available
    occupied,change please
    available
    occupied,change please
    


```python
#5-11
number = list(range(1,10))
for i in number:
    if i == 1:
        print(str(i)+'st')
    elif i == 2:
        print(str(i)+'nd')
    elif i == 3:
        print(str(i)+'rd')
    else:
        print(str(i)+'th')
```

    1st
    2nd
    3rd
    4th
    5th
    6th
    7th
    8th
    9th
    


```python
#5-12
print('略')
```

    略
    


```python
#5-13
print('略')
```

    略
    

### 第六章 字典


```python
#6.1
dic = {'first_name':'David', 'last_name':'Fincher', 'age':77, 'city':'New_York'}
print(dic)
```

    {'first_name': 'David', 'last_name': 'Fincher', 'age': 77, 'city': 'New_York'}
    


```python
#6.2
dic = {'libai':1, 'dufu':2, 'wangwei':3, 'baijuyi':4}
print(dic)
```

    {'libai': 1, 'dufu': 2, 'wangwei': 3, 'baijuyi': 4}
    


```python
#6.3
dic = {'append':'添加元素', 'insert':'插入元素', 'pop':'弹出元素', 'sort':'排列元素'}
print('append:\n\t'+dic['append'])
```

    append:
    	添加元素
    


```python
#6-4
for key, value in dic.items():
    print(key+':\n\t'+value)
```

    append:
    	添加元素
    insert:
    	插入元素
    pop:
    	弹出元素
    sort:
    	排列元素
    


```python
#6-5
rivers = {'huanghe':'China', 'nile':'Egypt', 'amazon':'Brazil'}
for key, value in rivers.items():
    print(key+' runs through '+value)
    print(key)
    print(value)
```

    huanghe runs through China
    huanghe
    China
    nile runs through Egypt
    nile
    Egypt
    amazon runs through Brazil
    amazon
    Brazil
    


```python
#6-6
names = ['baiqi', 'zhangyi', 'suqin', 'wangjian']
dic = {'baiqi':20, 'zhangyi':15}
for i in names:
    if i in dic.keys():
        print('thank you')
    else:
        print('please')
```

    thank you
    thank you
    please
    please
    


```python
#6-7
dic1 = {'baiqi':20, 'zhangyi':16, 'wangjian':14, 'fanju':5}
dic2 = {'libai':1, 'dufu':2, 'wangwei':3, 'baijuyi':4}
dic3 = {'tianwen':10, 'wuji':17, 'huangxie':13, 'zhaosheng':11}
guren = [dic1, dic2, dic3]
for i in guren:
    for k, g in i.items():
        print(k+':'+str(g))
```

    baiqi:20
    zhangyi:16
    wangjian:14
    fanju:5
    libai:1
    dufu:2
    wangwei:3
    baijuyi:4
    tianwen:10
    wuji:17
    huangxie:13
    zhaosheng:11
    


```python
#6-8
pet1 = {'name':'cat', 'age':2}
pet2 = {'name':'dog', 'age':3}
pet3 = {'name':'bird', 'age':4}
pets = [pet1, pet2, pet3]
for i in pets:
    for k, g in i.items():
        print(k+':'+str(g))
```

    name:cat
    age:2
    name:dog
    age:3
    name:bird
    age:4
    


```python
#6-9
place = {'baiqi':['xianyang', 'changping'], 'libai':['changan', 'taohuatan'], 'jifa':['haojing', 'qishan']}
for i in place.keys():
    print(i)
    for k in place[i]:
        print('He like '+k)
```

    baiqi
    He like xianyang
    He like changping
    libai
    He like changan
    He like taohuatan
    jifa
    He like haojing
    He like qishan
    


```python
#6-10
number = {'baiqi':[1, 2], 'libai':[3, 4], 'jifa':[5, 6]}
for i in number.keys():
    print(i)
    for k in number[i]:
        print('He like '+str(k))
```

    baiqi
    He like 1
    He like 2
    libai
    He like 3
    He like 4
    jifa
    He like 5
    He like 6
    


```python
#6-11
cities = {
            'changan':{'country':'tang', 'population':'100'},
            'beijing':{'country':'ming', 'population':'200'}, 
            'linan':{'country':'song', 'population':'150'}
            }
for i, k in cities.items():
    print(i)
    for m, n in k.items():
        print(m+ ' is '+n)
```

    changan
    country is tang
    population is 100
    beijing
    country is ming
    population is 200
    linan
    country is song
    population is 150
    


```python
#6-12
cities['luoyang'] = {'country':'han', 'population':'200'}
cities
```




    {'changan': {'country': 'tang', 'population': '100'},
     'beijing': {'country': 'ming', 'population': '200'},
     'linan': {'country': 'song', 'population': '150'},
     'luoyang': {'country': 'han', 'population': '200'}}



### 第七章 while循环


```python
#7-1
car = input('which car:')
print('we will see '+car)
```

    which car:sabaru
    we will see sabaru
    


```python
#7-2
num = input('how many')
if int(num) > 8:
    print('no seat')
else:
    print('ok')
```

    how many9
    no seat
    


```python
#7-3
num = input('give a number：')
if int(num)%10 == 0:
    print('yes')
else:
    print('please change')
```

    give a number：20
    yes
    


```python
#7-4
fruit = ''
while fruit != 'quit':
    fruit = input('give a fruit or quit:')
    print(fruit)
```

    give a fruit or quit:quit
    quit
    


```python
#7-5
age = ''
while age != 'quit':
    age = input('your age or quit:')
    if age == 'quit':
        print('quit')
    elif int(age) < 3:
        print('free')
    elif int(age) < 12:
        print(10)
    else:
        print(15)    
```

    your age or quit:quit
    quit
    


```python
#7-6
age = ''
while age != 'quit':
    age = input('your age or quit:')
    if age == 'quit':
        break
    elif int(age) < 3:
        print('free')
    elif int(age) < 12:
        print(10)
    else:
        print(15)  
```

    your age or quit:quit
    


```python
#7-8
sandwich = ['beef', 'vegatable', 'fruit']
finish = []
while sandwich:
    i = sandwich.pop()
    print(i+' done')
    finish.append(i)
print(finish)
print('all done')
```

    fruit done
    vegatable done
    beef done
    ['fruit', 'vegatable', 'beef']
    all done
    


```python
#7-9
sandwich = ['beef', 'vegatable', 'fruit', 'beef', 'beef']
print('beef out')
while 'beef' in sandwich:
    sandwich.remove('beef')
print(sandwich)
```

    beef out
    ['vegatable', 'fruit']
    


```python
#7-10
active = True
wish = {}
while active:
    name = input('your name:')
    place = input('your want:')
    wish[name] = place
    again = input('others?')
    if again == 'no':
        active = False
print(wish)   
```

    your name:ming
    your want:beijing
    others?no
    {'ming': 'beijing'}
    

### 第八章 函数


```python
#8-1
def display_message():
    print('python')
display_message()
```

    python
    


```python
#8-2
def favorite_book(title):
    print(' my favorite book is '+title)
favorite_book('Gone with the wind')
```

     my favorite book is Gone with the wind
    


```python
#8-3
def make_shirt(size,sign):
    print('the shirt is '+str(size)+' with '+sign)
make_shirt(99,'world'),make_shirt(sign='python', size=39)
```

    the shirt is 99 with world
    the shirt is 39 with python
    




    (None, None)




```python
#8-4
def make_shirt(size='big',sign='love'):
    print('the shirt is '+size+' with '+sign)
make_shirt(), make_shirt(size='middle'), make_shirt(sign='flash')
```

    the shirt is big with love
    the shirt is middle with love
    the shirt is big with flash
    




    (None, None, None)




```python
#8-5
def describe_city(city, country='China'):
    print(city+' is in '+country)
describe_city('beijing'), describe_city('shanghai'), describe_city('tokyo', 'japan')
```

    beijing is in China
    shanghai is in China
    tokyo is in japan
    




    (None, None, None)




```python
#8-6
def city_country(city, country):
    a = city +','+country
    return a
city_country('beijing','China'), city_country('shanghai','China'), city_country('paris', 'france')
```




    ('beijing,China', 'shanghai,China', 'paris,france')




```python
#8-7
def make_aublm(sing, name, num=''):
    if num == '':
        a = {sing:sing, name:name}
    else :
        a = {sing:sing, name:name, num:num}
    return a
make_aublm('zhoujielun', 'daoxiang'), make_aublm('wangfei', 'hongdou', '3')
```




    ({'zhoujielun': 'zhoujielun', 'daoxiang': 'daoxiang'},
     {'wangfei': 'wangfei', 'hongdou': 'hongdou', '3': '3'})




```python
#8-8
active = True
while active:
    sing = input('give sing:')
    name = input('give name:')
    num = input('give num:')
    make_aublm(sing, name, num)
    again = input('give other?')
    if again == 'no':
        active = False
```

    give sing:jay
    give name:qilixiang
    give num:2
    give other?no
    


```python
#8-9
magicians = ['alex', 'kim', 'frank', 'hook']
def show_magic(name):
    for i in name:
        print(i)
show_magic(magicians)
```

    alex
    kim
    frank
    hook
    


```python
#8-10
def make_great(names):
    n = 0
    for i in names:
        names[n] = 'the great '+ i
        n += 1
    return names
show_magic(make_great(magicians))
```

    the great alex
    the great kim
    the great frank
    the great hook
    


```python
#8-11
magicians = ['alex', 'kim', 'frank', 'hook']
new_magic = make_great(magicians[:])
show_magic(magicians), show_magic(new_magic)
```

    alex
    kim
    frank
    hook
    the great alex
    the great kim
    the great frank
    the great hook
    




    (None, None)




```python
#8-12
def sandwichs(*food):
    for i in food:
        print('you add '+i)
sandwichs('beef', 'fruit')
```

    you add beef
    you add fruit
    


```python
#8-13
def introduction(first_name, last_name, **message):
    print(first_name+ '_'+last_name)
    for key, value in message.items():
        print(key+':'+value)
introduction('frank', 'underwood', job='president', location='wasington')
```

    frank_underwood
    job:president
    location:wasington
    


```python
#8-14
def make_car(brand, style, **message):
    print(brand+ '_'+style)
    for key, value in message.items():
        print(key+':'+value)
make_car('sabaru', 'outback', color='blue', two_package='True')
```

    sabaru_outback
    color:blue
    two_package:True
    


```python
#8-15
print('略')
```

    略
    


```python
#8-16
print('略')
```

    略
    


```python
#8-17
print('略')
```

    略
    

### 第九章 类


```python
#9-1
class Restaurant():
    def __init__(self, name, cuisine_type):
        self.name = name
        self.cuisine_type = cuisine_type
    def describe_restaurant(self):
        print(self.name, self.cuisine_type)
    def open_restaurant(self):
        print('now is open')

huoguo = Restaurant('huoguo', 'hot')
print(huoguo.name)
print(huoguo.cuisine_type)
huoguo.describe_restaurant(), huoguo.open_restaurant()        
```

    huoguo
    hot
    huoguo hot
    now is open
    




    (None, None)




```python
#9-2
kaoyu = Restaurant('kaoyu', 'fish')
print(kaoyu.name)
print(kaoyu.cuisine_type)
kaoyu.describe_restaurant(), kaoyu.open_restaurant()
```

    kaoyu
    fish
    kaoyu fish
    now is open
    




    (None, None)




```python
#9-3
class User():
    def __init__(self, first_name, last_name, sex, age):
        self.first_name = first_name
        self.last_name = last_name
        self.sex = sex
        self.age = age
    def describe_user(self):
        print('name:'+self.first_name+'-'+self.last_name+'\nsex:'+self.sex+'\nage:'+self.age)
    def greet_user(self):
        print('hello,'+ self.first_name)

user1 = User('bruce', 'lee', 'male', '23')
user1.describe_user(), user1.greet_user()
```

    name:bruce-lee
    sex:male
    age:23
    hello,bruce
    




    (None, None)




```python
#9-4
class Restaurant():
    def __init__(self, name, cuisine_type):
        self.name = name
        self.cuisine_type = cuisine_type
        self.number_served = 0
    def describe_restaurant(self):
        print(self.name, self.cuisine_type)
    def open_restaurant(self):
        print('now is open')
    def set_number_served(self, num_guest):
        self.number_served = num_guest
    def incre_number_served(self, incre_guest):
        self.number_served += incre_guest

res = Restaurant('kaoyu', 'fish')
print(res.number_served)
res.set_number_served(10)
print(res.number_served)
res.incre_number_served(20)
print(res.number_served)
```

    0
    10
    30
    


```python
#9-5
class User():
    def __init__(self, first_name, last_name, sex, age):
        self.first_name = first_name
        self.last_name = last_name
        self.sex = sex
        self.age = age
        self.login_attempts = 0
    def describe_user(self):
        print('name:'+self.first_name+'-'+self.last_name+'\nsex:'+self.sex+'\nage:'+self.age)
    def greet_user(self):
        print('hello,'+ self.first_name)
    def incre_login_attempts(self):
        self.login_attempts += 1
    def reset_login_attempts(self):
        self.login_attempts = 0

user2 = User('gang', 'li', 'male', '55')
user2.incre_login_attempts()
print(user2.login_attempts)
user2.incre_login_attempts()
print(user2.login_attempts)
user2.incre_login_attempts()
print(user2.login_attempts)
user2.reset_login_attempts()
print(user2.login_attempts)
```

    1
    2
    3
    0
    


```python
#9-6
class IcecreamStand(Restaurant):
    def __init__(self, name, cuisine_type):
        super().__init__(name, cuisine_type,)
        self.flavors = ['apple', 'peach', 'banana']
    def show_flavors(self):
        for i in self.flavors:
            print(i)
            
ice1 = IcecreamStand('iceice', 'milk')
ice1.show_flavors
```




    <bound method IcecreamStand.show_flavors of <__main__.IcecreamStand object at 0x0000028970029B20>>




```python
#9-7
class Admin(User):
    def __init__(self, first_name, last_name, sex, age):
        super().__init__(first_name, last_name, sex, age)
        self.privileges = ['can add post', 'can deletew post', 'can ban user']
    def show_privileges(self):
        for i in self.privileges:
            print(i)
            
admin1 = Admin('conan', 'detective', 'male', '7')
admin1.show_privileges()
```

    can add post
    can deletew post
    can ban user
    


```python
#9-8
class Privilege():
    def __init__(self):
        self.privileges = ['can add post', 'can deletew post', 'can ban user']

class Admin(User):
    def __init__(self, first_name, last_name, sex, age):
        super().__init__(first_name, last_name, sex, age)
        self.privileges = Privilege().privileges
    def show_privileges(self):
        for i in self.privileges:
            print(i)

admin1 = Admin('conan', 'detective', 'male', '7')
admin1.show_privileges()
```

    can add post
    can deletew post
    can ban user
    


```python
#9-9
class Car():
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
    def get_describe(self):
        print('make:'+self.make+'\nmodel:'+self.model+'\nyear:'+self.year)
        
class Battery():
    def __init__(self, size=70):
        self.size = size
    def upgrade(self):
        if self.size == 85:
            self.size = self.size
        else:
            self.size = 85
    def get_range(self):
        if self.size == 70:
            drive_range = 240
        elif self.size == 85:
            drive_range = 270
        print(drive_range)

class E_car(Car):
    def __init__(self, make, model, year):
        super().__init__(make, model ,year)
        self.battery = Battery()

car1 = E_car('Tesla', 'Model_S', '2020')
car1.battery.get_range()
car1.battery.upgrade()
car1.battery.get_range()
```

    240
    270
    


```python
#9-10
print('略')
```

    略
    


```python
#9-11
print('略')
```

    略
    


```python
#9-12
print('略')
```

    略
    


```python
#9-13
from collections import OrderedDict
OD = OrderedDict()
OD['1'] = 'c'
OD['2'] = 'python'
OD['3'] = 'java'
for key, value in OD.items():
    print(key+'\n\t'+value)
```

    1
    	c
    2
    	python
    3
    	java
    


```python
#9-14
class Die():
    def __init__(self, side=6):
        self.side = side
    def roll_die(self):
        from random import randint
        num = randint(1,self.side)
        return num

die1 = Die(6)
die2 = Die(10)
die3 = Die(20)
dies = [die1, die2, die3]
for i in dies:
    result = []
    for k in range(10):
        x = i.roll_die()
        result.append(x)
    print(result)
```

    [4, 3, 2, 4, 6, 1, 6, 3, 5, 6]
    [8, 2, 2, 7, 10, 9, 9, 1, 7, 9]
    [8, 6, 12, 8, 20, 17, 10, 20, 3, 3]
    

### 第十章 文件异常


```python
print('略')
```

    略
    

### 第十一章 测试代码


```python
print('略')
```

    略
    

## 第二部分 项目


```python
print('略')
```

    略
    

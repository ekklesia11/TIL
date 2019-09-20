# [TIL] Python 3.7

---

\\# NUMBER

from copy import copy

print(7 // 4)  # returns an integer of the result

a = 10

a += 5

print(a)



\# STRING

print('=' * 50)

print('My Program')

print('=' * 50)



a = "Life is too short, You need Python"

print(len(a))

print('index test', a[3])

print('slicing test', 'the result is "' + a[0:4] + '"')

print(a[19:])  # You need Python

print(a[:17])



print('S' + a[13:17])



\# String Formatting

print('I eat %d apples.' % 50)  # %d >> i guess it is digits

print('I eat %s apples.' % 'ten')  # %s >> i guess it is string

number = 10

day = 'three'

print('I ate %d apples. so I was sick for %s days.' % (number, day))

\# %s String

\# %c charater

\# %d integer

\# %f floating-point >> 소수

\# %o Octal

\# %x Hex

\# >>> %% Literal % >> '%'



print('Error is %d%%.' % 98)

print('%10s' % 'hi')

print('%-10sjane' % 'hi')

print('%0.4f' % 3.42134234)



print('I eat {0} apples.'.format(number))

print('I eat {0} apples.'.format('five'))

print('I ate {0} apples. so I was sick for {1} days.'.format(number, day))

print('I ate {number} apples. so I was sick for {day} days.'.format(

​    number=10, day='three'))

print('I ate {0} apples. so I was sick for {day} days.'.format(8, day='three'))



print('{0:<10}'.format('hi'))  # left align

print('{0:>10}'.format('hi'))  # right align

print('{0:^10}'.format('hi'))  # center align

print('{0:=^10}'.format('hi'))  # center align filled with a character

print('{0:!<10}'.format('hi'))  # left align filled with a character

y = 3.42134234

print('{0:0.4f}'.format(y))

print('{{and}}')



name = '홍길동'

age = 30

print(f'나의 이름은 {name}입니다. 나이는 {age}입니다.')

print(f'나의 이름은 {name}입니다. 내년에 나이는 {age + 1}입니다.')



d = {'name': 'Daniel', 'age': 30}

print(f'나의 이름은 {d["name"]}입니다. 나이는 {d["age"]}입니다.')  # 객체에서는 큰따옴표를 써야하므로 주의하자



\# STRING METHOD

a = 'hobby'

print(a.count('b'))

a = 'Python is the best choice'

print(a.find('b'))  # returns first found index

print(a.find('k'))  # if it doesn't exist, return -1

print(a.index('t'))  # returns first found index

\# print(a.index('k'))  # throw error: subsring not found

print(','.join('abcd'))  # returns 'a,b,c,d'

print(' '.join('abcd'))  # returns 'a,b,c,d'

print(','.join(['a', 'b', 'c', 'd']))  # returns 'a, b, c, d'

print(a.upper())

print(a.lower())

b = '     hi     '

print(b.rstrip())  # .lstrip() or rstrip() >>> left trim or right trim

print(b.strip())  # trim all spaces

print(a.replace('Python', 'Javascript'))

print(a.split())

c = 'a-b-c-d'

print(c.split('-'))



\# LIST : Data MUTABLE

\# indexing slicing >>> same as above string

a = [1, 2, 3]

b = [4, 5, 6]

print(a + b)  # list concat

print(a * 3)  # list repeat

print(len(a))  # list length

print(str(238945723985))  # converting number to string

b[2] = 10  # change specific list value >>> reference type?

print(b)

del a[1]  # delete specific list value

print(a)

a = [1, 2, 3, 4, 5]

del a[2:]  # delete from index number, 2

print(a)

a.append(6)  # add value to the list

print(a)

a = [4, 3, 6, 1, 2, 5]

a.sort()  # mutable

print(a)

a = ['f', 'd', 'a', 'c', 'b']

a.sort()

print(a)

a.reverse()  # mutable

print(a)

a.insert(0, 1000)  # insert 1000 at 0th index

a.insert(3, 777)  # insert 777 at 3rd index

print(a)

a.remove('d')  # delete or remove 'd' found first

print(a)

print(a.pop())  # returns last value in the list and delete it

print(a)

print(a.pop(1))  # returns 1st index value and delete it

print(a)

print(a.count(777))

a.extend([4, 5])  # a concat with -->> it must be a list when use .extend(LIST)

print(a)



\# TUPLE : All data is IMMUTABLE

t1 = ()

t2 = (1,)  # if there only one value, ',' must present at the end

t3 = (1, 2, 3)

t4 = 1, 2, 3  # paranthesis can be ignored

t5 = ('a', 'b', ('ab', 'cd'))

print(t4 + t5)

print(t4[1:])

print(t4 * 3)

print(len(t4))



\# DICTIONARY : Object from JavaScript

d = {'key': 'value'}

d['newKey'] = 'newValue'  # add new key-value pair

print(d)

del d['newKey']  # delete key-value from dictionary

print(d)

d[1, 2, 3] = 'tuple key-value pair'

print(d)

\# returns keys in an object form >>> dict_keys(['key', (1, 2, 3)])

print(d.keys())

print(list(d.keys()))  # returns keys in a list

for k in d.keys():

​    print(k)

print(d.values())  # returns values in an object form

print(d.items())  # returns (key, value) >> tuple form

print(type(list(d.items())[1]))  # type check

d.clear()  # clear all key-value pairs

print(d)  # now it is empty dictionary

a = {'a': 1, 'b': 2}

print(a['a'])

print(a.get('a'))

print(a.get('c'))  # returns None not error

\# check if it is True or False >> python uses capital letter for boolean type

print(a.get('a') == a['a'])

\# if value is none, it returns default value 'not found value'

print(a.get('c', 'not found value'))

print('a' in a)  # returns boolean

print('c' in a)



\# SET : no repeat, no order

l = [1, 2, 3, 4, 4]

print(set(l))  # no repeat >>> {1, 2, 3, 4}

str = 'Hello'

print(set(str))  # no repeat no order >> returns random order each calling

s1 = set([1, 2, 3, 4, 5, 6])

s2 = set([4, 5, 6, 7, 8, 9])

print(s1 & s2)  # 교집합

print(s1.intersection(s2))

print(s1 | s2)  # 합집합 no repeat values

print(s1.union(s2))

print(s1 - s2)  # 차집합

print(s2 - s1)

print(s1.difference(s2))

print(s2.difference(s1))

s1.add(100)  # add a value to the set1

print(s1)

s1.update([333, 999, 500])  # add many values

print(s1)

s1.remove(100)  # remove specific value in a set

print(s1)



\# BOOL

print(type(True))  # >>> <class 'bool'> -->> bool === boolean

print(type(False))

a = [1, 2, 3, 4]



while a:

​    print(a.pop())



if []:

​    print('TRUE')

else:

​    print('FALSE')



if [1, 2, 3]:

​    print("참")

else:

​    print("거짓")



print(bool('python'))  # True

print(bool(''))  # False

print(bool([]))

print(bool(0))

print(bool(3))  # True



\# VARIABLES

variable = 'assigned value'

print(variable)

a = [1, 2, 3]

print(id(a))  # the address at where the varible pointing

b = a  # pointing the same address id

print(b)

a[1] = 10

print(b)  # it's 1st index will be 10 too because they are pointing the same address

b = a[:]

a[1] = 200

print(a)

print(b)  # b doesn't change because they have different address id

print(id(a) == id(b))  # >>> False



\# MODULES

'''

from copy import copy  # importing copy module >>> due to pylint it goes to the top

'''

b = copy(a)

print(b)



\# VARIABLES using tuple or list

a, b = ('python', 'life')  # a, b = 'python', 'life' -->> works too

\# c, d = ['javascript', 'latte'] -->> works too

[c, d] = ['javascript', 'latte']

print(a)

print(b)

print(c)

print(d)



a = b = 'hey'

print(a, b)



a = 3

b = 5

a, b = b, a

print(a, b)  # swapping values



\# PRACTICE NO.1

\# Q1

국어 = 80

영어 = 75

수학 = 55

average = (국어 + 영어 + 수학) / 3

print(average)  # 70.0

print('%0.0f' % average)  # 70

\# Q2

if 13 % 2 == 0:

​    print(True)

else:

​    print(False)

\# Q3

id = '881120-1068234'

bornDate = '19' + id[:6]

codeId = id[7:]

print(bornDate, codeId)

\# Q4

pin = '881120-1068234'

if pin[7] == '1':

​    print('male')

else:

​    print('female')

\# Q5

a = 'a-b-c-d'

a = a.replace('-', '#')  # it can change all '-' value like g flag

print(a)

\# Q6

a = [1, 3, 5, 4, 2]

a.sort()

a.reverse()

print(a)

\# Q7

a = ['Life', 'is', 'too', 'short']

print(' '.join(a))

\# Q8

a = 1, 2, 3

b = (4,)

a = a + b

print(a)

\# Q9

a = dict()

a['name'] = 'python'

a[('a',)] = 'python'

\# a[[1]] = 'python'  # error due to the key [1] is a list and it is mutable

a[250] = 'python'

print(a)

\# Q10

a = {'A': 90, 'B': 80, 'C': 70}

print(a.pop('B'))

print(a)  # 'B' key-value deleted after pop

\# Q11

a = [1, 1, 1, 2, 2, 3, 3, 3, 4, 4, 5]

s = set(a)

print(s)

a = list(s)

print(a)

\# Q12

a = b = [1, 2, 3]

a[1] = 4

print(a == b)  # True [1, 4, 3]





'''

==, >, <, <=, >=, !=

"value1" and "value2", "value1" or "value2", not "value"

"value" in, "value" not in (list, tuple, string)

'''



money = 15

if money:

​    print('take a cap')

else:

​    print('walk home, man')



if money > 5 and money < 10:

​    print('take a bus')

elif money > 10:

​    print('take a cap')

else:

​    print('walk home man')



\# conditional expression

score = 50

message = 'success' if score > 60 else 'FAIL'

print(message)



\# WHILE : same as FOR

treeHit = 0

while treeHit < 10:

​    treeHit += 1

​    print("나무를 %d번 찍었습니다." % treeHit)

​    if treeHit == 10:

​        print("나무 넘어갑니다.")



prompt = '''

\1. Add

\2. Del

\3. List

\4. Quit



Enter number: '''



\# number = 0

\# while number != 4:

\#     print(prompt)

\#     number = int(input())



coffee = 10

money = 300

while money:

​    print('here it is, sir')

​    coffee -= 1

​    print('only %dcoffee left' % coffee)

​    if coffee == 0:

​        print('no coffee')

​        break



\# continue : going back to the first line of while condition

a = 0

while a < 10:

​    a += 1

​    if a % 2 == 0:

​        continue

​    print(a)



\# FOR

test_list = ['one', 'two', 'three']

for i in test_list:

​    print(i)



a = [(1, 2), (3, 4), (5, 6)]

for (first, last) in a:

​    print(first + last)



marks = [90, 25, 67, 45, 80]



number = 0

for mark in marks:

​    number += 1

​    if mark >= 60:

​        print("%d번 학생은 합격입니다." % number)

​    else:

​        print("%d번 학생은 불합격입니다." % number)



marks = [90, 25, 67, 45, 80]



number = 0

for mark in marks:

​    number += 1

​    if mark < 60:

​        continue

​    print("%d번 학생 축하합니다. 합격입니다. " % number)



\# range function

add = 0

for i in range(0, 10):

​    add += 1

print(add)



for number in range(len(marks)):

​    if marks[number] < 60:

​        continue

​    print('%d번 합격!' % (number + 1))



for i in range(2, 10):

​    for j in range(1, 10):

​        print(i*j, end=" ")  # end=" " 줄바꿈 없이 이어지도록 만들기 위해 추가된다.

​    print('')  # 줄바꿈



\# List comprehension

a = [1, 2, 3, 4]

result = []

for i in range(len(a)):

​    result.append(a[i] * 3)



print(result)



a = [1, 2, 3, 4]

result = [num * 3 for num in a]

print(result)



a = [1, 2, 3, 4]

result = [num * 3 for num in a if num % 2 == 0]

\# [return what, while, if] multiple while can be used as below

print(result)



result = [num * int for num in a

​          for int in range(1, 6)]

print(result)



\# PRACTICE NO.2

\# Q1

a = "Life is too short, you need python"



if "wife" in a: print("wife")

elif "python" in a and "you" not in a: print("python")

elif "shirt" not in a: print("shirt")

elif "need" in a: print("need")

else: print("none")

\# >>> 'shirt'

\# Q2

count = 1

result = 0

while count < 1000:

​    count += 1

​    if count % 3 == 0:

​        result += count

print(result)

\# Q3

count = 1

while count <= 10:

​    print('*' * count)

​    count += 1

\# Q4

for i in range(1, 101):

​    print(i)

\# Q5

A = [70, 60, 55, 75, 95, 90, 80, 80, 85, 100]

result = 0

for score in A:

​    result += score

print(result / len(A))

\# Q6

numbers = [1, 2, 3, 4, 5]

result = []

for n in numbers:

​    if n % 2 == 1:

​        result.append(n*2)



result = [n * 2 for n in numbers if n % 2 == 1]

print(result)





def addition(a, b):

​    return a + b



print(addition(3, 4))



def say():

​    return 'hi'



print(say())



def adding(a, b):

​    print(f'{a} 와(과) {b} 를 더하면 {a + b} 이(가) 됩니다.')

\# def adding(a, b):

\#     print('%d 와(과) %d 를 더하면 %d 이(가) 됩니다.' % (a, b, a + b))

\# def adding(a, b):

\#     print('{0} 와(과) {1} 를 더하면 {2} 이(가) 됩니다.'.format(a, b, a + b))

adding(10, 4)



def greet():

​    print('hello world')



greet()



\# Rest parameter in Python

def add_many(*args): # *rest parameters become tuple

​    print(args)

​    result = 0

​    for i in args:

​        result += i

​    print(result)



add_many(1, 2, 3, 4, 5, 6, 7, 8, 10)



\# returning tuple

def makeTuple(a, b):

​    return a * 5, b * 6



print(makeTuple(10, 5))



result1, result2 = makeTuple(3, 7)

print(result1, result2)



\# default value

def say_myself(name, old, man=True): 

​    print("나의 이름은 %s 입니다." % name) 

​    print("나이는 %d살입니다." % old) 

​    if man: 

​        print("남자입니다.")

​    else: 

​        print("여자입니다.")



say_myself('daniel', 30, False)



\# outer variable cannot be used in a function

\# all variables in a function are independent

a = 1

def vartest(n):

​    a = n + 1

​    return a



print(vartest(5))

print(a)



\# how to change global variable by using a function

\# NOT recommended

a = 10

def changeA(n):

​    global a

​    a = a + n



changeA(10)

print(a) # 20



\# RECOMMENDED

a = 10

def changeN(n):

​    n = n + 10

​    return n



a = changeN(10) 

print(a) # 20



\# lambda == def and it returns too // like JS ES6 arrow function

add = lambda a, b: a + b

result = add(3, 4)

print(result)



\# user input function

\# name = input('what is your name? ')

print(name)  # input value assigned to name



\# PRINT usage

print("This", "is", "sparta")



\# PRACTICE NO.3

\# Q1

def is_odd(n):

​    if n % 2 == 1:

​        return True

​    else:

​        return False



print(is_odd(9))

\# Q2

def getAverage(*value):

​    result = 0

​    for v in value:

​        result += v

​    return result / len(value)



print(getAverage(1, 2, 3, 4, 5, 6, 7, 8, 9, 10))

\# Q3

\# input1 = int(input("첫번째 숫자를 입력하세요:"))

\# input2 = int(input("두번째 숫자를 입력하세요:"))



\# total = input1 + input2

\# print("두 수의 합은 %s 입니다" % total)

\# Q4

print("you" "need" "python")

print("you"+"need"+"python")

print("you", "need", "python") # ',' join them with a space between words

print("".join(["you", "need", "python"]))



\# codingdojang questions

result = 0

for i in range(1, 1000):

​    if i % 3 == 0 or i % 5 == 0:

​        result += i

print(result)
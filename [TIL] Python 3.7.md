# [TIL] Python 3.7

---

\# NUMBER

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

c = 'a:b:c:d'

print(c.split(':'))
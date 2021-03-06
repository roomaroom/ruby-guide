**Ruby** — це інтерпретована, повністю об'єктно-орієнтована мова програмування, Мова відрізняється високою ефективністю розробки програм і увібрала в себе кращі риси Perl, Java, Python, Smalltalk, Eiffel, Ada і Lisp. Мова була створена Юкіхіро Мацумото, котрий почав працювати над Ruby 24 лютого 1993 року. Метою було створення об'єктно-орієнтованої, легкої в розробці, інтерпретованої мови програмування. Перша загальнодоступна версія 0.95 побачила світ 1995 року. «Ruby» був названий так через жарт, що ходив у колі друзів Мацумото, і був ілюзією до назви мови програмування Perl (перлина)



**Ідеологія Ruby:**
- люди відрізняються один від одного, тому існує кілька способів вирішення однієї задачі. Кожен вибирає той спосіб, який йому до душі; 
- досвідчені програмісти не повинні стикатися з несподіваною поведінкою програм (принцип найменшого подиву); 
- програмування має приносити задоволення. Всі рутинні нижче дії повинні виконуватися комп'ютером. 
- Не дублюй код (DRY - don't repeat yourself)
- KISS (англ. keep it simple, stupid — «не ускладнюй, дурню» або більш ввічливий варіант англ. keep it short and simple — «роби коротше і простіше»)
- Не зроби велосипеда. 
- Рубісти діляться своїм кодом, досвідом і готовими рішеннями

**RVM — Ruby Version Manager** Програма для управління версіями Ruby.     
встановити curl - *sudo apt-get install curl libcurl3 libcurl3-dev php5-curl*  
встановити rvm  - https://rvm.io/rvm/install   
source ~/.rvm/scripts/rvm
echo "source $HOME/.rvm/scripts/rvm" >> ~/.bash_profile
rvm list - список версій рубі 
rvm install ruby 2.2.3 - встановити рубі 2.2.3

**gem - пакет (файл) з бібліотекою або додатком.** Має стандартизований вигляд і розташований в сховище в мережі. https://rubygems.org/gems
gem install devise

```
irb
puts "Hello world"
```

##локальні змінні
можуть мати  a-z или '_'
```
name = 'Ivan'
```

##константа  A-Z
```
NAME = 'Ivan'
```

Змінні Ruby містять не самі об'єкти, а посилання на них. Присвоєння — це не передача значення, а копіювання посилання на об'єкти. Наприклад:
```
a = "abcdefg"   =>   "abcdefg"
b = a           =>   "abcdefg"
b               =>   "abcdefg"
a[3] = 'R'      =>   "R"
b               =>   "abcRefg"
```

#Типи Даних Числові
##1. Integer:  
Fixnum (цілі числа, менші 2{30})
```
123 # Fixnum
```
Bignum (цілі числа, великі 2{30})
```
12345678901234567890 # Bignum
```
##2. Float
```
2.1
```
##Арифметичні операції
Арифметичні операції в Ruby звичайні: складання (+), віднімання (-), множення (*), ділення (/), отримання залишку від ділення (%), піднесення до степеня (**).
```
6 + 4  # => 10
6 - 4  # => 2
6 * 4  # => 24
6/4    # => 1
6 % 4  # => 2
6 ** 4 # => 1296
```
Операції з привласненням
```
number_one = number_one + number_two
number_one += number_two
```
##Методи явного перетворення типів  
to_f Перетворити в число з плаваючою комою   
to_i Перетворити в ціле  
to_s Перетворити в рядок   
to_a Перетворити в масив  

```
7.to_f      #=> 7.0
7.9.to_i    #=> 7
7.to_s      #=> "7"
"7".to_a    #=> ["7"]
```
###Випадкове число
```
rand(100) 
```

##Строка String
```
name = "Ruby"
```
Рядок створюється за допомогою обмежувальних знаків. Для цих цілей найчастіше використовуються "(програмістська лапки) і '(машинописний апостроф). Їхній зміст різний. Рядок в апострофа гарантує, що в ній буде міститися той же текст, що і в коді програми, без змін. Рядок в лапках буде проходити попереднє перетворення. Будуть розкриті конструкції «вставка» і «спеціальний символ».

Вставка - це хитра конструкція, яка вставляється  всередині рядка. Вона складається з комбінації октоторп і двох фігурних дужок **# {'тут був Василь'}**
```
my_number = 18
puts 'Моє число = ' + my_number.to_s
puts "Моє число = #{my_number}"
```
Методи стрічок, їх дуже багато http://ruby-doc.org/core-2.2.0/String.html#method-i-encode
```
name = 'Ivan'
name.size
name.empty?
name.reverse
"Ку-ку".split('-')
```
#Масив Array
```
numbers = [1, 2, 3, 4, 5, 6]
ary = [ "fred", 10, 3.14, "This is a string", "last element"]
ary[0]
ary.first
art.last
numbers.sort
[1, 2, 3, 4] + [5, 6, 7] + [8, 9]
[1, 1, 2, 2, 3, 3, 3, 4, 5] - [1, 2, 4]
[1, 2, 3, 4, 5, 5, 6, 0, 1, 2, 3, 4, 5, 7].uniq 

ary.each do | i |
   puts i
end

ary.each {|i| puts i} 
art_new = ary.map{ |elem| elem * 2 }
```
##Блоки
Блок - це довільний код, який можна передати будь-якого методу як неявний останнього аргументу.
Код може перебувати всередині фігурних дужок {} або ключових слів do end
```
def say_hello
 yield
end

say_hello { puts "hello" }
```
##Hash Type
```
hash = {5=>3, 1=>6, 3=>2}
hash[5]                      #=> 3
hash[2]                      #=> nil 
hash[3]                      #=> 2

hsh.each do | key, value |
   print key, "is", value, "\ n"
end
```

##Range Type
```
0 .. 5 

(10..15).each do | n |
   print n, ''
end
```
##Symbol Type
Синтаксично зазвичай позначається двокрапкою (:), за яким йде ідентифікатор
```
user = :vigor 
```
Символи - це специфічні рядки, які в програмі id вказується один раз і на завжди.
Вони легше і в деяких місцях зручніше. Символи дозволяють економити пам'ять
```

"vigor".object_id # => 70122132113780

"vigor".object_id # => 70122132113340 
# OBJECT_ID has changed!

user = :vigor 
:vigor.object_id 

user = :vigor 
user.object_id

array = ["foo", "foo", "foo", :foo, :foo, :foo]
hash = {:name => 'Ivan', :age => 20}
hash = { name: 'Ivan', age: 20}
```
Типове застосування символів - для представлення імені змінної або методу і як ключі в хеші

##Методи
```
def name(variable)
  puts variable
end

To call a methods

name variable
or
name(variable)

def hi
 puts "Hello World!"
end

hi
```
##Цикл
```
for i in 1...10
   print i, " Hello\n";
end 
```
##Conditional statemen
```
if cond
  # code to do
end
///////////

if cond
   puts "x is 2"
else
   puts "I can't guess the number"
end


unless cond
  # code to do
end

age = 3
case $age
when 0..2
  puts "baby"
when 3..6
  puts "little child"
when 7..12
  puts "child"
when 13..18
  puts "youth"
else
  puts "adult"
end
```
##times
```
3.times do
 puts 'Ура!'
end
```

**Об’єктно-орієнтоване програмування (ООП)** — це метод програмування, оснований на поданні програми у вигляді сукупності взаємодіючих об’єктів, кожен з яких є екземпляром певного класу  

**Клас** – визначає  характеристики деякої сутності та дії, які вона здатна виконувати (її поведінки, методи або можливості).
```
class Car
end
```

Наприклад, клас Машина може характеризуватись рисами, притаманними всім машинам, зокрема: колір, ціна, модель.

![image](https://bparanj.gitbooks.io/ruby-basics/content/car-concept.png)

Добавимо поведінку
```
class Car
  def drive
    'driving'
  end
end
```
![image](https://bparanj.gitbooks.io/ruby-basics/content/defining-method.png)

Аналогія класа автомобіля

Клас автомобіля схожий на  план.

![image](https://bparanj.gitbooks.io/ruby-basics/content/car-bluprint.png)

**Об’єкт** – окремий екземпляр класу, який характреизується станом і поведінкою

Об'єкт Автомобіль схожий на реальний автомобіль, зроблений з використанням  плану створення автомобіля(нашого класу).
```
class Car 
  def drive
    return 'driving'
  end
end

car = Car.new

p car.drive
```
Ми маємо поведінку автомобіля але нам бракує стану автомобіля(параметрів), наприклад колір, встановимо через це змінні екземпляра

**Змінні екземпляра(Instance Variable)** - це змінні об'єкта, такі змінні починаються з @  
Локальні змінні методу є чинними до завершення методу. З іншого боку, змінні екземпляра кожного об'єкта будуть дійсні, поки існує об'єкт
```
class Car 
  def set_color(color)
    @color = color
  end
  
  def drive
    return 'driving'
  end
end

car = Car.new

car.set_color('red')

p car
```
Але це трохи не логічно, бо колір автомобіля задається при створенні автомобіля а не пізніше, тому використовують для цього конструктори.

**Конструктор класу** - це спеціальний метод класу, який автоматично викликається при створенні об'єкта.
Призначення конструктора — встановити початковий стан об'єкта шляхом ініціалізації атрибутів об'єкта.
```
class Car
  def initialize(color = 'green')
    @color = color
  end
  
  def drive
    'driving'
  end
end

car = Car.new('red')
```
![image](https://bparanj.gitbooks.io/ruby-basics/content/part1/color-instance-variable.png)

**Створення об'єкта**
```
car = Car.new('red')
p Car.instance_variables
```
![image](https://bparanj.gitbooks.io/ruby-basics/content/part1/car-instance.png)

##Інкапсуляція 
доступ до стану об'єкта напряму заборонено, і ззовні з ним можна взаємодіяти виключно через заданий інтерфейс (відкриті поля та методи), що дозволяє знизити зв'язність. Таким чином контролюються звернення до полів класів та їхня правильна ініціалізація, усуваються можливі помилки пов'язані з неправильним викликом метод

```
class Person

  def initialize(first_name, last_name)
    @first_name = first_name
    @last_name = last_name
  end
  
  #setter
  def first_name=(first_name)
    @first_name = first_name
  end
  
  #getter
  def first_name
    @first_name
  end
  
  def hello
    puts "Hello Ruby! from #{@first_name} #{@last_name}"
  end
end
```
```
class Person
  attr_accessor :first_name, :last_name

  def initialize(first_name, last_name)
    @first_name = first_name
    @last_name = last_name
  end
  
  def hello
    puts "Hello Ruby! from #{@first_name} #{@last_name}"
  end
end

person = Person.new('Ivan','Shevchenko')
```
**Інкапсуляція поведінки** поведінки здійснюється за допомогою обмеження доступу
до методів.

Класифікація методів:
- public - загальні методи. Загальні методи дозволяють об'єктам взаємодії-
вать один з одним. Вони можуть бути викликані в будь-якій області видимості;
- private - приватні методи. Приватні методи реалізують внутрішню логіку об'єкта. Вони можуть бути викликані тільки в області видимості класу. Приватні методи допомагають приховувати реалізацію роботи
програми і дозволити доступ тільки до API.

```
class Person
  def initialize(first_name, last_name)
    @first_name = first_name
    @last_name = last_name
  end
  
  def hello
    puts "Hello Ruby! from #{full_name}"
  end
  
  private
  
  def full_name
    "#{@first_name} #{@last_name}"
  end
end

person = Person.new('Ivan','Shevchenko')
```
##Наслідування
**Наслідування** – процес, завдяки якому один об’єкт може придбати властивості іншого, тобто наслідувати властивість іншого обєкту і додавати риси характерні тільки для нього самого.
```
class Mammal  
  def breathe  
    puts "inhale and exhale"  
  end  
end  
  
class Cat < Mammal  
  def speak  
    puts "Meow"  
  end  
end  
  
rani = Cat.new  
rani.breathe  
rani.speak  
```
##Поліморфізм
**Поліморфізм** - так називають явище, при якому функції(методу) з одним і тим же ім'ям відповідає різний програмний код (поліморфний код) в залежності від того, об'єкт якого класу використовується при виклику даного методу.
```
class Person
  def initialize(first, last, age)
    @first_name = first
    @last_name = last
    @age = age
  end

  def birthday
    @age += 1
  end

  def introduce
    puts "Hi everyone. My name is #{@first_name} #{@last_name}."
  end
end

class Student < Person
  def introduce
    puts "Hello teacher. My name is #{@first_name} #{@last_name}."
  end
end

class Teacher < Person
  def introduce
    puts "Hello class. My name is #{@first_name} #{@last_name}."
  end
end

class Parent < Person     
  def introduce    
    super
    puts "Hi. I'm one of the parents. My name is #{@first_name} #{@last_name}."     
  end 
end 

john = Student.new("John", "Doe", 18) 
john.introduce   #=> Hello teacher. My name is John Doe.

ivan = Parent.new("Ivan", "Doe", 18) 
ivan.introduce
```

##Змінні класу
Змінні класу починаються із @@. Змінні класів відрізняються від змінних екземпляра класу тим, що будучи оголошені в будь-якому місці, їх областю видимості буде клас і всі його екземпляри.
```
class MyClass
  @@value = 1
  
  def add_one
    @@value += 1
  end

  def value
    @@value
  end
end

instanceOne = MyClass.new
instanceTwo = MyClass.new

puts instanceOne.value
instanceOne.add_one

puts instanceOne.value
puts instanceTwo.value
```
##Методи класу
записуються як  
```
def self.methodname
end
```
```
class Box
  @@count = 0
   
  def initialize(w, h)
    @@count += 1
    
    @width, @height = w, h
  end

  def self.print_count 
    puts "Box count is: #{@@count}"
  end
end

# Create two objects
box1 = Box.new(10, 20)
box2 = Box.new(30, 100)

Box.print_count

Box.class_variables
box2.instance_variables
```
##Модулі в ruby
Модулі в ruby за своєю суттю схожі на класи. Модулі являють собою збірник різних методів, констант і т.п., але на відміну від класів не можна створювати екземпляри об'єктів з модулів. Зате описану в модулі функціональність можна додавати до функцій класу або об'єкта. Модулі призначені для того щоб спростити дизайн програми і надати їй гнучкість і уникнути дублювання коду.
###include
```
module  RandomNumbers 
  def generate 
    rand(10)
  end 
end

class  Diceg
  include  RandomNumbers 
end

class  Raceg
   include  RandomNumbers 
end

d = Diceg.new
d.generate  

r = Raceg.new
r.generate 
```
###extend
```
module  RandomNumbers 
  def generate 
    rand(10)
  end 
end

class  Diceg
  extend RandomNumbers 
end

class  Raceg
  extend  RandomNumbers 
end

Diceg.generate 


Raceg.generate

```

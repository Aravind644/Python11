# Python11
this and super


1.Print the fields/instance members of the current class using this and without using object

class Test: 
    def __init__(self, a, b): 
        self.a = a 
        self.b = b 
      
    def __repr__(self): 
        return "Test a:% s b:% s" % (self.a, self.b) 
    
    def __str__(self): 
        return "From str method of Test: a is % s, " \ 
              "b is % s" % (self.a, self.b) 
  
# Driver Code         
t = Test(1234, 5678) 
  
# This calls __str__() 
print(t) 
  
# This calls __repr__() 
print([t])



2.Print the fields/instance members of the parent class using super

class Parent():
    def __init__(self):
        self.myvar = 1

class Child(Parent):
    def __init__(self):
        Parent.__init__(self)

        # here you can access myvar like below.
        print (self.myvar)

child = Child()
print (child.myvar)




3.Call constructor of the current class using this()

# defining class A
class A:
  def __init__(self, txt):
    print(txt, 'I am in A Class')
  
# B class inheriting A
class B(A):
  def __init__(self, txt):
    print(txt, 'I am in B class')
    super().__init__(txt)
      
# C class inheriting B
class C(B):
  def __init__(self, txt):
    print(txt, 'I am in C class')
    super().__init__(txt)
  
# D class inheriting B
class D(B):
  def __init__(self, txt):
    print(txt, 'I am in D class')
    super().__init__(txt)
  
# E class inheriting both D and C
class E(D, C):
  def __init__(self):
    print( 'I am in E class')
    super().__init__('hello ')
  
# driver code
d = E()
print('')
h = C('hi')




4.Call argument constructor of current class using this()

class Configurator():
    config_file = "" #variable which stores config file
    input_response = "" #variable which stores input response json

    def __init__(self,config_file, input_response):
        self.config_file = config_file
        self.input_response = input_response

        config = ConfigParser.ConfigParser()
        config.read('config.cfg')
        if config.get('Configurator', 'ctool')  ==  'Chef':
            Configurator.__initialize(self)

    def __initialize(self):
        open_input_response = open(self.input_response, 'r')
        read_cloudprovider = json.load(open_input_response)
        cloudprovider = read_cloudprovider['CloudProvider']
        if cloudprovider == 'AWS':
            print('Working Here')
            obj = AWS()
            obj.print_test(self)


class AWS(Configurator):
    def print_test(self):
        print('I am AWS Class')


def main():
    configurator = Configurator('config.cfg', 'input_response.json')


if __name__ == '__main__':
    main()
    
    
    
    
5.Call constructor of the parent class using super()

class Class():
    def __init__(self, x):
        print(x)
  
# this is the subclass of class "Class"
class SubClass(Class):
    def __init__(self, x):
  
        # this is how we call super
        # class's constructor
        super().__init__(x)
  
# driver code
x = [1, 2, 3, 4, 5]
a = SubClass(x)





6.Use this() and super() in methods not in constructors

 class Grand:
  def fun(self):
      print('grand')
      return
class Parent(Grand):
  def fun(self)
    super().fun()
    print('parent')
    return
class child(Parent):
  def fun(self)
    super().fun()
    print('child')
    return
class inheritance:
  def main():
    obj=child()
    obj.fun()
    return
inheritance.main()


# PolymorphismDemo

demo for polymorphism in C++
[reference](https://www.udemy.com/share/1000hGA0MSdVdUR3w=/)

a. overloading:
```cpp
//overloading
int GetSize(int x)
{
	return x;
}

int GetSize(std::string x)
{
	return x .length();
}

```

b. runtime polymorphism:
```cpp
//runtime polymorphism

class Animal
{

public:
	virtual void MakeNoise()
	{
		std::cout << GetSize("Animal noise.") << std::endl;
	}
};

class Dog : public Animal 
{

public:
	void MakeNoise() override
	{
		std::cout << "Woof." << std::endl;
	}
};

class Cat : public Animal
{

public:
	void MakeNoise() override 
	{
		std::cout << "Meow." << std::endl;
	}
};

void Stroke(Animal* animal)
{
	animal->MakeNoise();
}

int main()
{
    std::cout << GetSize(5)<<std::endl; 
	std::cout << GetSize("hello world") << std::endl;
	Dog dog;
	Cat cat;
	Stroke(&dog);
	Stroke(&cat);
	return 0;
}
```

![polymorphism](https://github.com/SeokLeeUS/PolymorphismDemo/raw/master/_images/polymorphism.png)


c. another example 
```cpp
#include <iostream>

class Base
{
public:
    virtual void BeginPlay() const
    {
        std::cout << "Base::BeginPlay called\n";
    }
};

class Derived : public Base
{
    using Super = Base;
public:
    void BeginPlay() const override
    {
        Super::BeginPlay(); //comment out this line to see difference
        std::cout << "Derived::BeginPlay called\n";
    }
};

int main()
{
    Derived D;
    D.BeginPlay();
}

```



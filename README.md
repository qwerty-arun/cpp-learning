# C++ (Intermediate Level)
- Some Intermediate Stuff which are useful will be discussed here

# List of Topics
## Smart Pointers
- Typically, when we use `new`, we have to use `delete` in case of raw pointers
- Smart pointers does it automatically
- Types of smart pointers: `std::unique_ptr`,  `std::shared_ptr` and `std::weak_ptr`.
- include `<memory>`

## std::unique_ptr
- Memory gets free as scope ends.
- You cannot copy them.
### Example
```cpp
#include <memory>
class Player
{
  Player()
  {
    std::cout<<"Player Created\n";
  }

  ~Player()
  {
    std::cout<<"PLayer Destroyed\n";
  }

  void function()
  {
    std::cout<<"Inside Function\n";
  }
};

int main()
{
  {
    unique_ptr<Player> ptr1(new User());
    unique_ptr<Player> ptr2 = make_unique<Player>();
    ptr1->function();
    ptr2->function();
  }
    std::cout<<"Outside code\n";
  return 0;
}
```
## std::shared_ptr and std::weak_ptr
### Example
```cpp
#include <memory>
class Player
{
  Player()
  {
    std::cout<<"Player Created\n";
  }

  ~Player()
  {
    std::cout<<"PLayer Destroyed\n";
  }

  void function()
  {
    std::cout<<"Inside Function\n";
  }
};

int main()
{
  {
    shared_ptr<Player> ptr1(new User()); //bad stuff
    shared_ptr<Player> ptr2 = make_shared<Player>();
    shared_ptr<Player> ptr3 = ptr2;
    weak_ptr<Player> ptr4 = ptr3;
    ptr1->function();
    ptr2->function();
  }
    std::cout<<"Outside code\n";
  return 0;
}
```

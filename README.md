# project-5-Java
Generic Code for Java
Collections can store Objects of any Type
Generics restricts  the Objects to be put in a collection 
Generics ease identification of runtime errors at compile time

A simple code example:
class QueueOfStrings {
   private LinkedList<String> items = new LinkedList<String>();
   public void enqueue(String item) {
      items.addLast(item);
   }
   public String dequeue() {
      return items.removeFirst();
   }
   public boolean isEmpty() {
      return (items.size() == 0);
   }
}

A simple generic method:
public static int countOccurrences(String[] list, String itemToCount) {
   int count = 0;
   if (itemToCount == null) {
      for ( String listItem : list )
         if (listItem == null)
            count++;
   }
   else {
      for ( String listItem : list )
         if (itemToCount.equals(listItem))
            count++;
   }
   return count;
}
Let's consider...
I have an Animal class, where each Animal can have many friends.
And subclasses like Dog, Duck, Mouse etc which add specific behavior like bark(), quack() etc.

Here's the Animal class:

public class Animal {
    private Map<String,Animal> friends = new HashMap<>();

    public void addFriend(String name, Animal animal){
        friends.put(name,animal);
    }

    public Animal callFriend(String name){
        return friends.get(name);
    }
}
Mouse jerry = new Mouse();
jerry.addFriend("spike", new Dog());
jerry.addFriend("quacker", new Duck());

((Dog) jerry.callFriend("spike")).bark();
((Duck) jerry.callFriend("quacker")).quack();
public <T extends Animal> T callFriend(String name, Class<T> type) {
    return type.cast(friends.get(name));
}
jerry.callFriend("spike", Dog.class).bark();
jerry.callFriend("quacker", Duck.class).quack();

These are examples of generic classes and methods. 

# singleton-Pattern
"Create a Singleton class called Logger that allows only one instance to be created. It should have a function called logMessage() that prints a custom message passed by the user. Demonstrate this in the main() function."

class Logger private constructor(){
  companion object{
  private var instance:Logger?=null
  fun getInstance():Logger{
    if(instance == null){
      instance = Logger()
    }
    return instance!!
  }
}
fun logMessage(){
  println("user login")
}
}
fun main(){
   val logger1 = Logger.getInstance()
    logger1.logMessage()

    val logger2 = Logger.getInstance()
    logger2.logMessage() 
}
-------------------------------------------------------question2-------------------------------------------------------
👩🏻‍💻 Design a UserSession class using the Singleton pattern in Kotlin.
It should only allow one session at a time.
Include a function startSession(username: String) that prints:

👉 "Session started for [username]"

Then in main(), try creating two sessions and see if it still prints the same session instance or not.

class UserSession private constructor(){
  companion object{
  private var session:UserSession?=null 
  fun getSession():UserSession{
    if(session == null){
      session = UserSession()
    }
    return session!!
  }
}
fun startSession(username:String){
  println("session started for $username")
}
}
fun main(){
  val a = UserSession.getSession()
 
  a.startSession("fatima")
}

------------------------------------------------------------------------------------------Question3-------------------------------------------------------------

class Printer private constructor(){
  companion object{
    private var instance:Printer?=null
    fun getInstance():Printer{
      if(instance == null){
        instance = Printer()
      }
      return instance!!
    }
  }
  fun printDocument(documentName:String){
    println("printing document $documentName")
  }
}
fun main(){
  val a = Printer.getInstance()
  a.printDocument("kotlin")
  val b = Printer.getInstance()
  b.printDocument("java")
}

----------------------------------------------------------------------question---------------------------------------------------------

// Create a Kotlin class named LibraryBook with the following:

// 🔐 Properties:
// bookTitle → title of the book (String)

// author → name of the author (String)

// isAvailable → Boolean (true if the book is available, false if borrowed)

// 🧰 Functions:
// borrowBook() → marks the book as borrowed if it's available

// returnBook() → marks the book as returned

// checkAvailability() → prints whether the book is available or no


class LibraryBook(val bookTitle:String,    private val author:String){

    private var isAvailable:Boolean=true
    
    fun borrowBook(){
      if(isAvailable==true){
          isAvailable=false
          println("book is borrowed")
      }else{
      println("book is already borrowed")
    }
}
fun returnBook(){
    if(!isAvailable){
        isAvailable=true
        println("book is returned")
    }else{
        println("book is not borrowed")
    }
    
}
fun checkAvailability(){
    if(isAvailable){
       println("book is available") 
    }else{
        println("book is not available")
    }
}
}
fun main() {
    val book = LibraryBook("Atomic Habits", "James Clear")
    book.checkAvailability()
    book.borrowBook()
    book.borrowBook()
    book.returnBook()
    book.checkAvailability()
}
-----------------------------------------------------------------------------------------question------------------------------------------------------------
// orderItems → Mutable list of Strings (e.g., ["Burger", "Fries"])

// isDelivered → Boolean (initially false)

// 🧰 Functions:
// addItem(item: String) → Adds a food item to the order

// removeItem(item: String) → Removes an item if it exists

// deliverOrder() → Marks the order as delivered

// viewOrder() → Prints all items in the order + status (delivered or not


class FoodOrder(val customerName:String){
  private var orderItems: MutableList<String> = mutableListOf()
  private var isDelivered:Boolean=false
  
  fun addItem(item:String){
      orderItems.add(item)
      println("order added ")
  }
  fun removeItem(item:String){
      if(orderItems.contains(item)){
          orderItems.remove(item)
          println("item is removed")
      }else{
          println("item was not present in list")
      }
  }
  fun deliverOrder(){
      if(!isDelivered){
          isDelivered=true
          println("order delivered")
      }else{
          println("order is already deliverd")
      }
  }
  
  

}
fun main() {
    val myOrder = FoodOrder("fatima")
    myOrder.deliverOrder()     // First call → should deliver
    myOrder.deliverOrder()     // Second call → should say already delivered
}


--------------------------------------------------------------------------------Question-----------------------------------------------------------------------------------------
// Create a class called GroceryCart that:

// Properties:
// cartOwner: String

// items: MutableList<String> (starts as an empty list)

// isCheckedOut: Boolean (default is false)

// Functions:
// addItem(item: String) — adds the item to the cart.

// removeItem(item: String) — removes the item if it's in the cart.

// viewCart() — prints all items in the cart.

// checkout() — sets isCheckedOut = true and prints confirmation. 
// If already checked out, print a message that checkout is already don
class GroceryCart(val cartOwner:String){
    private var items:MutableList<String> = mutableListOf()
     private var isCheckedOut:Boolean= false
     
     fun addItem(item:String){
         items.add(item)
         println("item added")
     }
     fun removeItem(item:String){
     if(items.contains(item)){
         items.remove(item)
         println("item removed")
     }else{
         println("item was not present")
     }
}
fun viewCart(){
    for(i in items){
        println(i)
    }
}
fun checkout(){
    if(!isCheckedOut){
        isCheckedOut=true
        println("checkout")
    }else{
        println("checkout already done")
    }
}
}
fun main(){
    val a = GroceryCart("fatima")
    a.addItem("juice")
    a.viewCart()
    a.checkout()
}



# KotlinScript
Yes, I know that kts exists, however that is a JVM thing, and this is supposed to be something that
can even run in a browser.

DISCLAIMER: I do not plan on duplicating the entire Kotlin language, just like JavaScript is not a
duplicate of Java. This is a new language that is inspired by Kotlin, but is not a copy of it.

Currently, this repo is pretty empty, but I plan on making it look like this:

```
// Everything that is not a keyword needs to be imported, even println
import { fetch, println, FetchData.json, writeToFile, deleteFile } from std
import { getType } from reflection

fun main() {
    // const -> perm(anent) in this language
    perm a = fetch("https://example.com/api/data").json()
    // short types are there for convenience 
    var b: str = a["key"]
    var c: String = a["key"]
    assert b == c
    println(b)
    
    // This is taken from Kotlin
    a.forEach { key, value ->
        println("$key: $value")
    }
    
    // Functions are of Type Runnable, and so are lambdas
    // Yes, the hottest🔥 feature of Kotlin also exists here, and yes unicode is allowed
    assert getType { println("Hello") } == getType(main)
    
    // You can "pipe" args into functions, if the previous function errors it will not call the next
    // There are short try-catch blocks. No try catch creates hard errors
    try fetch("https://example.com") > println("Example.com: \n $it")
    catch println("Failed to fetch example.com") 
    
    try fetch("https://example.com/api/data").json() > writeToFile("data.json")
    catch println("Failed to fetch data")
    // This will run even though there will be an error
    defer deleteFile("data.json")
    
    // This will error
    fetch("https://doesnotexist.com")
}

// The way how OOP will work is not yet decided
```
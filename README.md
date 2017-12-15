# Questions
### 1
```
class Test {

    companion object {
        // @JvmStatic


        class CountingSet<T>(
                val innerSet: MutableCollection<T> = HashSet<T>()
        ) : MutableCollection<T> by innerSet {

            var objectsAdded = 0

            override fun add(element: T): Boolean {
                objectsAdded++
                return innerSet.add(element)
            }

            override fun addAll(c: Collection<T>): Boolean {
                objectsAdded += c.size
                innerSet.addAll(c)
                println(c.size) // 5
                println(innerSet.size) // 4
                return true
            }

            override val size: Int
                get() {
                    println(innerSet.size) // 4
                    return innerSet.size
                }
        }

        @JvmStatic
        fun main(args: Array<String>) {
            val cset = CountingSet<Int>()
            val k = listOf(1, 1, 2, 45, 34)
            cset.addAll(k)
            println("${cset.objectsAdded} objects were added, ${cset.size} remain, ${k.size}")
        }


    }
}
```

### 2
```
class Test {

    companion object {
        // @JvmStatic

    }


}

fun salute() {

}


fun main(args: Array<String>) {
    run(::salute)
}
```
### 3
```
class Test {

    companion object {


        @JvmStatic
        fun main(args: Array<String>) {
            val list = listOf("a", "ab", "b")
            println(list.groupBy(String::first))
        }

    }


}

```
### 4
```
import java.util.ArrayList

fun main(args: Array<String>) {
    val numbers = ArrayList<Int>()
    numbers.add(1)
    numbers.add(1)
    numbers += 42
    println(numbers[0].toString() + " " + numbers[1])
}

```

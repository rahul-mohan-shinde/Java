# Complete Java Backend Developer Interview Questions
## 5-Month Roadmap - Question-Based Learning

---

# 📌 MONTH 1: CORE JAVA QUESTIONS

## Variables, Data Types & Operators

**1. What's the difference between primitive and non-primitive data types?**
- **Primitive**: Store actual values (int, char, boolean, float, double, byte, short, long)
- **Non-primitive**: Store references/addresses (String, Arrays, Classes, Interfaces)
- Primitive are faster, stored in stack memory; Non-primitive stored in heap

**2. What are the types of type casting? Explain implicit vs explicit.**
- **Implicit (Widening)**: Automatic conversion from smaller to larger type
  ```java
  int x = 10;
  long y = x;  // Automatic
  ```
- **Explicit (Narrowing)**: Manual conversion from larger to smaller type
  ```java
  double d = 10.5;
  int x = (int) d;  // Manual casting
  ```

**3. What's the difference between `==` and `.equals()`?**
- `==`: Compares memory addresses (references) for objects, values for primitives
- `.equals()`: Compares actual content/value of objects
```java
String s1 = new String("Hello");
String s2 = new String("Hello");
s1 == s2;      // false (different objects)
s1.equals(s2); // true (same content)
```

**4. Difference between logical operators (&&, ||) and bitwise operators (&, |)?**
- **Logical**: Work on boolean values, short-circuit evaluation
  - `&&` stops if first condition is false
  - `||` stops if first condition is true
- **Bitwise**: Work on bits, no short-circuit
  - `&` and `|` evaluate both operands always

**5. What's the output of `System.out.println(10 + 20 + "Hello")`? Why?**
- Output: `30Hello`
- Reason: Left to right evaluation. First `10+20=30` (integer addition), then `30+"Hello"` (string concatenation)

**6. What's the output of `System.out.println("Hello" + 10 + 20)`?**
- Output: `Hello1020`
- Reason: Once string appears, everything becomes string concatenation

---

## Control Statements & Arrays

**7. Why use `break` in switch statement? What is fall-through?**
- **break**: Exits switch block after matching case
- **Fall-through**: Without break, execution continues to next cases
```java
switch(day) {
    case 1: 
    case 2: 
    case 3: System.out.println("Weekday"); // Fall-through
            break;
}
```

**8. When to use for-each loop? What are limitations?**
- Use for: Iterating through Collections/Arrays without index
- Limitations:
  - Can't modify elements while iterating
  - Can't get index
  - Works only forward direction
  - Can't remove elements directly

**9. How is 2D array stored in memory?**
- Row-major order (stored as array of arrays)
- Each row is a separate array object in heap
- Non-contiguous memory allocation

**10. Why does ArrayIndexOutOfBoundsException occur? How to avoid?**
- Occurs when accessing index >= length or negative index
- Prevention: Always check array length before accessing
```java
if(index >= 0 && index < array.length) {
    // safe access
}
```

---

## Methods & OOP Basics

**11. How to achieve method overloading? Can we change return type?**
- Achieved by: Different number of parameters, different types, different order
- Return type alone CANNOT overload methods
- Compiler uses method signature (name + parameter list) for resolution

**12. What is constructor chaining? How to use `this()` and `super()`?**
- Constructor chaining: Calling one constructor from another
- `this()`: Calls constructor of same class
- `super()`: Calls parent class constructor
- Must be first statement in constructor

**13. How to achieve encapsulation? Give example.**
- Make fields private
- Provide public getters and setters
```java
public class Employee {
    private String name;
    public String getName() { return name; }
    public void setName(String name) { this.name = name; }
}
```

**14. Why doesn't Java support multiple inheritance? How do interfaces solve it?**
- **Diamond Problem**: Confusion if both parent classes have same method
- **Solution**: Multiple interfaces allowed because they only declare methods, no implementation conflict
- Java 8+ default methods can cause conflict, resolved by explicit override

**15. Difference between abstract class and interface? When to use what?**
| Feature | Abstract Class | Interface |
|---------|---------------|-----------|
| Variables | All types | public static final |
| Methods | Abstract + Concrete | Abstract (default/static in Java 8+) |
| Inheritance | Single | Multiple |
| Constructor | Yes | No |
| Use when | Common base with shared code | Contract/behavior definition |

**16. Explain access modifiers with scope.**

| Modifier | Same Class | Same Package | Subclass | Anywhere |
|----------|------------|--------------|----------|----------|
| private | ✓ | ✗ | ✗ | ✗ |
| default | ✓ | ✓ | ✗ | ✗ |
| protected | ✓ | ✓ | ✓ | ✗ |
| public | ✓ | ✓ | ✓ | ✓ |

---

## String & Exception Handling

**17. Why is String immutable? What are benefits?**
- **Reasons**: Security, Thread safety, Caching (String pool), Performance
- **Benefits**:
  - Thread-safe inherently
  - Can be shared safely
  - HashCode caching improves performance
  - Class loading security

**18. Difference between String, StringBuilder, StringBuffer? Performance comparison?**
| Feature | String | StringBuilder | StringBuffer |
|---------|--------|---------------|--------------|
| Mutability | Immutable | Mutable | Mutable |
| Thread-safe | Yes | No | Yes |
| Performance | Slow | Fastest | Fast |
| Use when | Constant values | Single thread | Multi-thread |

**19. What's the flow of `try-catch-finally`? When doesn't finally execute?**
- Flow: try → catch (if exception) → finally (always)
- Finally doesn't execute when:
  - System.exit() called
  - JVM crashes
  - Thread dies

**20. Difference between Checked and Unchecked exceptions? Give examples.**
| Type | Checked | Unchecked |
|------|---------|-----------|
| Compile-time | Yes | No |
| Must handle | Yes | Optional |
| Extends | Exception | RuntimeException |
| Examples | IOException, SQLException | NullPointerException, ArithmeticException |

**21. How to create custom exception? Difference between `throw` and `throws`?**
```java
class CustomException extends Exception {
    public CustomException(String msg) {
        super(msg);
    }
}
```
- **throw**: Used to actually throw exception object
- **throws**: Declares that method might throw exception

---

# 📌 MONTH 2: COLLECTIONS + MULTITHREADING + SQL

## Collections Framework

**22. ArrayList vs LinkedList - performance comparison? When to use what?**

| Operation | ArrayList | LinkedList |
|-----------|-----------|------------|
| Access | O(1) - Fast | O(n) - Slow |
| Insert/Delete (end) | O(1) - Amortized | O(1) |
| Insert/Delete (middle) | O(n) - Slow | O(1) - Fast |
| Memory | Less overhead | More overhead |

- **Use ArrayList**: Frequent access, less manipulation
- **Use LinkedList**: Frequent insertion/deletion, sequential access

**23. How does HashMap work internally? Role of equals() and hashCode()?**
- **Internal**: Array of Node<K,V> (buckets)
- **Process**:
  1. Calculate hashCode() → index in array
  2. If bucket empty → store directly
  3. If collision → store as LinkedList/Tree
  4. equals() checks equality in collision
- **Equals-HashCode contract**: If equals() true, hashCode() must be same

**24. How does HashSet detect duplicates?**
- Uses HashMap internally (keys are elements, value is dummy object)
- Checks hashCode() and equals() to determine if key exists
- If exists → element not added

**25. TreeMap vs HashMap - difference? How does sorting work?**
| Feature | HashMap | TreeMap |
|---------|---------|---------|
| Order | No order | Sorted (natural/comparator) |
| Performance | O(1) | O(log n) |
| Null keys | One null allowed | Not allowed |
| Implementation | Hashing | Red-Black tree |
| Use when | Fast access | Sorted keys needed |

**26. Comparable vs Comparator - difference? Real example?**
- **Comparable**: Natural ordering (implements `compareTo()`)
  ```java
  class Student implements Comparable<Student> {
      public int compareTo(Student s) {
          return this.id - s.id;
      }
  }
  ```
- **Comparator**: Custom ordering (implements `compare()`)
  ```java
  Comparator<Student> byName = (s1, s2) -> s1.name.compareTo(s2.name);
  ```

**27. Why does ConcurrentModificationException occur? Solution?**
- Occurs when modifying collection while iterating (except using iterator's remove)
- **Solutions**:
  - Use `Iterator.remove()`
  - Use Concurrent Collections (CopyOnWriteArrayList, ConcurrentHashMap)
  - Use synchronized block

---

## Multithreading

**28. Thread class vs Runnable interface - which is better and why?**
- **Runnable is better** because:
  - Can extend other classes (Java doesn't support multiple inheritance)
  - Better separation of concerns
  - Can be used with ExecutorService
  - Reusable

**29. What are thread lifecycle states?**
1. **NEW**: Thread created but not started
2. **RUNNABLE**: Ready to run or running
3. **BLOCKED**: Waiting for lock
4. **WAITING**: Waiting indefinitely (wait(), join())
5. **TIMED_WAITING**: Waiting for specified time (sleep(timeout))
6. **TERMINATED**: Execution complete

**30. Why need synchronization? How does synchronized keyword work?**
- **Need**: Multiple threads accessing shared resource → data inconsistency
- **Working**: Acquires lock on object/method
- Only one thread can execute synchronized block at a time
- Other threads get BLOCKED state

**31. What is deadlock? Give example and how to avoid?**
- **Deadlock**: Two threads waiting for each other's locks forever
- **Example**:
  ```java
  Thread1: lock A → lock B
  Thread2: lock B → lock A
  ```
- **Prevention**:
  - Lock ordering (always acquire locks in same order)
  - Lock timeout using tryLock()
  - Avoid nested synchronized blocks

**32. What are benefits of ExecutorService over Thread class?**
- Thread pool management (reuse threads)
- Better performance (thread reuse → less overhead)
- Task submission and scheduling
- Shutdown gracefully
- Return results using Future

**33. Callable vs Runnable - difference? What is Future?**
| Feature | Runnable | Callable |
|---------|----------|----------|
| Return | void | Returns value |
| Exception | Can't throw checked | Can throw checked |
| Method | run() | call() |
- **Future**: Represents result of async computation, used with Callable

---

## Java 8 Features

**34. What is Lambda expression? How related to Functional Interface?**
- Lambda: Anonymous function (-> syntax)
- Functional Interface: Interface with single abstract method
- Lambda provides implementation of that single method
```java
// Without Lambda
Runnable r1 = new Runnable() { public void run() { ... } };
// With Lambda
Runnable r2 = () -> { ... };
```

**35. What is Stream API? Use of map(), filter(), reduce()?**
- **Stream**: Process collections functionally
- **map()**: Transform each element
- **filter()**: Select elements based on condition
- **reduce()**: Combine elements to single result
```java
list.stream()
    .filter(i -> i > 5)
    .map(i -> i * 2)
    .reduce(0, Integer::sum);
```

**36. Why use Optional? How does it prevent NullPointerException?**
- Optional: Container that may or may not contain non-null value
- Forces explicit null handling
```java
Optional<String> opt = Optional.ofNullable(str);
opt.ifPresent(s -> System.out.println(s));
String result = opt.orElse("Default");
```

---

## SQL

**37. Explain SQL joins with examples - INNER, LEFT, RIGHT, FULL?**
```sql
-- INNER: Only matching records
SELECT * FROM Employees e 
INNER JOIN Departments d ON e.dept_id = d.id;

-- LEFT: All employees + matching departments
SELECT * FROM Employees e 
LEFT JOIN Departments d ON e.dept_id = d.id;

-- RIGHT: All departments + matching employees
SELECT * FROM Employees e 
RIGHT JOIN Departments d ON e.dept_id = d.id;

-- FULL: All records from both
SELECT * FROM Employees e 
FULL JOIN Departments d ON e.dept_id = d.id;
```

**38. GROUP BY vs ORDER BY - difference?**
- **GROUP BY**: Groups rows with same values, used with aggregate functions
- **ORDER BY**: Sorts result set
```sql
SELECT department, COUNT(*) 
FROM employees 
GROUP BY department 
ORDER BY COUNT(*) DESC;
```

**39. HAVING vs WHERE - when to use what?**
| Feature | WHERE | HAVING |
|---------|-------|--------|
| Filters | Individual rows | Group results |
| Aggregate | Cannot use | Can use |
| Order of execution | Before GROUP BY | After GROUP BY |
```sql
-- WHERE filters before grouping
SELECT * FROM employees WHERE salary > 50000;

-- HAVING filters after grouping
SELECT department, AVG(salary) 
FROM employees 
GROUP BY department 
HAVING AVG(salary) > 50000;
```

**40. Subquery vs Join - which is better and why?**
- **JOIN is usually better** because:
  - Better performance (optimized by query planner)
  - More readable
  - Can use indexes effectively
- **Subquery use when**: Need to compare aggregate results, need EXISTS checks

**41. What is Index? Types and benefits? Performance impact?**
- **Index**: Data structure improving retrieval speed
- **Types**: B-Tree, Hash, Bitmap, Clustered, Non-Clustered
- **Benefits**: Faster SELECT queries
- **Cost**: Slower INSERT/UPDATE/DELETE, extra storage

**42. What is Normalization? Explain 1NF, 2NF, 3NF?**
- **1NF**: Atomic values, unique rows
- **2NF**: 1NF + No partial dependency (all non-key attributes depend on full PK)
- **3NF**: 2NF + No transitive dependency (non-key attributes depend only on PK)

---

# 📌 MONTH 3: JDBC + SPRING CORE + SPRING BOOT

## JDBC

**43. What are JDBC steps from connection to data fetch?**
```java
// 1. Load Driver
Class.forName("com.mysql.cj.jdbc.Driver");

// 2. Get Connection
Connection conn = DriverManager.getConnection(url, user, pass);

// 3. Create Statement
Statement stmt = conn.createStatement();

// 4. Execute Query
ResultSet rs = stmt.executeQuery("SELECT * FROM users");

// 5. Process Result
while(rs.next()) {
    String name = rs.getString("name");
}

// 6. Close Resources
rs.close(); stmt.close(); conn.close();
```

**44. Statement vs PreparedStatement - which is better and why?**
- **PreparedStatement is better** because:
  - Prevents SQL Injection
  - Better performance (pre-compiled, reusable)
  - Easier to set parameters

**45. What is SQL Injection? How does PreparedStatement prevent it?**
- **SQL Injection**: Malicious SQL code inserted in input
- **Prevention**: PreparedStatement uses parameterized queries
- Input is treated as data, not executable code
```java
// Vulnerable
String query = "SELECT * FROM users WHERE id = " + userInput;

// Safe
PreparedStatement ps = conn.prepareStatement("SELECT * FROM users WHERE id = ?");
ps.setInt(1, userInput);
```

**46. Transaction management in JDBC? commit() and rollback()?**
```java
conn.setAutoCommit(false);
try {
    // Multiple updates
    stmt.executeUpdate("UPDATE accounts SET balance = balance - 100 WHERE id = 1");
    stmt.executeUpdate("UPDATE accounts SET balance = balance + 100 WHERE id = 2");
    conn.commit(); // Save all changes
} catch(Exception e) {
    conn.rollback(); // Undo all changes
}
```

---

## Spring Core

**47. What is IoC (Inversion of Control)? How implemented in Spring?**
- **IoC**: Objects don't create dependencies, container provides them
- **Implementation**: Spring Container manages object lifecycle
- **Dependency Injection** is the design pattern for IoC

**48. Types of Dependency Injection?**
1. **Constructor Injection** (Recommended)
   ```java
   @Component
   public class UserService {
       private final UserRepository repo;
       public UserService(UserRepository repo) {
           this.repo = repo;
       }
   }
   ```
2. **Setter Injection**
3. **Field Injection** (Not recommended - hard to test)

**49. Difference between `@Component`, `@Service`, `@Repository`, `@Controller`?**
| Annotation | Purpose |
|------------|---------|
| @Component | Generic stereotype for any bean |
| @Service | Business logic layer |
| @Repository | Data access layer (adds exception translation) |
| @Controller | Web layer (handles HTTP requests) |

**50. What are bean scopes in Spring?**
| Scope | Description |
|-------|-------------|
| Singleton | One instance per container (Default) |
| Prototype | New instance each request |
| Request | One instance per HTTP request |
| Session | One instance per HTTP session |
| Application | One instance per ServletContext |

**51. How does `@Autowired` work? When to use `@Qualifier`?**
- `@Autowired`: Spring finds and injects dependency by type
- `@Qualifier`: Used when multiple beans of same type exist
```java
@Autowired
@Qualifier("specialService")
private Service service;
```

---

## Spring Boot

**52. How does Spring Boot auto-configuration work?**
- Based on dependencies in classpath
- Reads `META-INF/spring.factories`
- Conditional configuration using `@Conditional` annotations
- Can override by configuring `application.properties`

**53. application.properties vs application.yml - difference?**
```properties
# properties file
server.port=8080
spring.datasource.url=jdbc:mysql://localhost/db
```
```yaml
# yaml file (more readable)
server:
  port: 8080
spring:
  datasource:
    url: jdbc:mysql://localhost/db
```

**54. Spring Boot layered architecture explain.**
```
Controller Layer (REST endpoints)
        ↓
 Service Layer (Business Logic)
        ↓
Repository Layer (Data Access)
        ↓
      Database
```

**55. `@RestController` vs `@Controller` - difference?**
| Feature | @RestController | @Controller |
|---------|-----------------|-------------|
| Response | JSON/XML directly | View name |
| Has @ResponseBody | Yes | No |
| Use for | REST APIs | MVC with view templates |

**56. How to implement validation?**
```java
public class User {
    @NotNull(message = "Name is required")
    private String name;
    
    @Email(message = "Invalid email")
    private String email;
}

@PostMapping("/users")
public ResponseEntity create(@Valid @RequestBody User user) {
    // ...
}
```

**57. How to handle global exceptions?**
```java
@ControllerAdvice
public class GlobalExceptionHandler {
    
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity handleNotFound(ResourceNotFoundException ex) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND).body(ex.getMessage());
    }
    
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity handleValidation(MethodArgumentNotValidException ex) {
        return ResponseEntity.badRequest().body(ex.getBindingResult().getAllErrors());
    }
}
```

---

# 📌 MONTH 4: REST API + JPA + SECURITY

## REST API

**58. What are REST API principles?**
1. **Stateless**: Each request has all needed info
2. **Client-Server**: Separation of concerns
3. **Cacheable**: Responses can be cached
4. **Uniform Interface**: Consistent API design
5. **Layered System**: Multiple layers possible
6. **Code on Demand** (optional)

**59. `@RequestMapping` vs `@GetMapping` - difference?**
- `@RequestMapping`: Generic mapping (method specified separately)
- `@GetMapping`: Specific for GET requests (shortcut)
```java
@RequestMapping(value = "/users", method = RequestMethod.GET)
@GetMapping("/users") // Same thing
```

**60. `@PathVariable` vs `@RequestParam` - when to use?**
```java
// @PathVariable: URL path segment
GET /users/123
@GetMapping("/users/{id}")
public User get(@PathVariable Long id) { ... }

// @RequestParam: Query parameter
GET /users?id=123
@GetMapping("/users")
public User get(@RequestParam Long id) { ... }
```

**61. Why use ResponseEntity? Benefits?**
- Full control over HTTP response
- Set status codes, headers, body
```java
return ResponseEntity
    .status(HttpStatus.CREATED)
    .header("Location", "/users/1")
    .body(user);
```

**62. What is DTO? Why use it? Separate from Entity?**
- **DTO**: Data Transfer Object - carrier of data between layers
- **Reasons**:
  - Hide sensitive data
  - Reduce over-fetching/under-fetching
  - Decouple internal representation from API contract
  - Add validation specific to API

**63. Explain HTTP status codes.**
| Code | Meaning | Use |
|------|---------|-----|
| 200 | OK | Successful request |
| 201 | Created | Resource created |
| 400 | Bad Request | Invalid request |
| 401 | Unauthorized | Authentication required |
| 403 | Forbidden | Not enough permissions |
| 404 | Not Found | Resource doesn't exist |
| 500 | Internal Server Error | Server error |

---

## JPA/Hibernate

**64. JPA vs Hibernate - difference? What is ORM?**
- **JPA**: Specification (interface)
- **Hibernate**: Implementation of JPA
- **ORM**: Object-Relational Mapping - maps Java objects to DB tables

**65. How to map entity relationships?**
```java
// OneToOne
@OneToOne
@JoinColumn(name = "address_id")
private Address address;

// OneToMany (Bidirectional)
@OneToMany(mappedBy = "department")
private List<Employee> employees;

// ManyToOne
@ManyToOne
@JoinColumn(name = "department_id")
private Department department;

// ManyToMany
@ManyToMany
@JoinTable(
    name = "student_course",
    joinColumns = @JoinColumn(name = "student_id"),
    inverseJoinColumns = @JoinColumn(name = "course_id")
)
private List<Course> courses;
```

**66. Lazy vs Eager loading - difference? Performance impact?**
- **Eager**: Loads related data immediately (fetch = FetchType.EAGER)
- **Lazy**: Loads related data on demand (fetch = FetchType.LAZY)
- **Performance**: Lazy is better (load only what needed), but watch for N+1 problem

**67. What is N+1 query problem? Solution?**
- **Problem**: 1 query for parent + N queries for each child
- **Solution**:
  - `@EntityGraph` or `@NamedEntityGraph`
  - `JOIN FETCH` in JPQL
  - Batch fetching

**68. JPQL vs Native SQL - which is better?**
| Feature | JPQL | Native SQL |
|---------|------|------------|
| Database independent | Yes | No |
| Uses entity names | Yes | No |
| Type-safe | Yes | No |
| Performance | Generally good | Can be optimized |
- **Use JPQL** for portability, **Native** for DB-specific features

**69. How to implement pagination?**
```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    Page<User> findByAgeGreaterThan(int age, Pageable pageable);
}

// Usage
PageRequest pageable = PageRequest.of(page, size, Sort.by("name").descending());
Page<User> users = repository.findByAgeGreaterThan(18, pageable);
```

---

## Spring Security

**70. Authentication vs Authorization - difference?**
- **Authentication**: Who you are (login process)
- **Authorization**: What you can do (permissions)

**71. What is BCryptPasswordEncoder? How to store passwords?**
- BCrypt: One-way hashing algorithm with salt
- Automatically adds random salt to prevent rainbow table attacks
```java
@Bean
public PasswordEncoder passwordEncoder() {
    return new BCryptPasswordEncoder();
}
// Store: encoder.encode("password")
// Verify: encoder.matches(rawPassword, encodedPassword)
```

**72. What is JWT structure? Header, Payload, Signature?**
```
JWT = Header.Payload.Signature
- Header: Algorithm (HS256, RS256) + token type
- Payload: Claims (user info, expiration)
- Signature: HMACSHA256(base64UrlEncode(header) + "." + base64UrlEncode(payload), secret)
```

**73. Explain JWT authentication flow.**
1. **Login**: User sends credentials → Server validates
2. **Token Generation**: Server creates JWT with user info
3. **Client stores token** (localStorage/cookie)
4. **Subsequent requests**: Client sends JWT in Authorization header
5. **Server validates** JWT for each request
6. **Server extracts** user info from JWT

**74. How to implement role-based access?**
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            .authorizeHttpRequests(authz -> authz
                .requestMatchers("/api/admin/**").hasRole("ADMIN")
                .requestMatchers("/api/users/**").hasAnyRole("USER", "ADMIN")
                .requestMatchers("/public/**").permitAll()
                .anyRequest().authenticated()
            )
            .oauth2ResourceServer(oauth2 -> oauth2.jwt());
        return http.build();
    }
}

// Method level
@PreAuthorize("hasRole('ADMIN')")
public void deleteUser(Long id) { ... }
```

**75. How does Spring Security filter chain work?**
```
Request → 
Filter1 (UsernamePasswordAuthenticationFilter) → 
Filter2 (BearerTokenAuthenticationFilter) → 
... → 
FilterN → 
DispatcherServlet → 
Controller
```

---

# 📌 MONTH 5: DSA + GIT + PROJECTS

## DSA Questions (Most Asked)

**76. Find missing number in array (1 to n).**
```java
public int findMissing(int[] arr, int n) {
    int totalSum = n * (n + 1) / 2;
    int actualSum = 0;
    for(int num : arr) actualSum += num;
    return totalSum - actualSum;
}
```

**77. Reverse a string without inbuilt function.**
```java
public String reverse(String str) {
    char[] chars = str.toCharArray();
    int left = 0, right = chars.length - 1;
    while(left < right) {
        char temp = chars[left];
        chars[left] = chars[right];
        chars[right] = temp;
        left++; right--;
    }
    return new String(chars);
}
```

**78. Find duplicate elements in array.**
```java
public List<Integer> findDuplicates(int[] arr) {
    Set<Integer> seen = new HashSet<>();
    List<Integer> duplicates = new ArrayList<>();
    for(int num : arr) {
        if(!seen.add(num)) duplicates.add(num);
    }
    return duplicates;
}
```

**79. Check if string is palindrome.**
```java
public boolean isPalindrome(String str) {
    int left = 0, right = str.length() - 1;
    while(left < right) {
        if(str.charAt(left) != str.charAt(right)) return false;
        left++; right--;
    }
    return true;
}
```

**80. Find middle element of linked list in single pass.**
```java
public ListNode findMiddle(ListNode head) {
    ListNode slow = head, fast = head;
    while(fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    return slow;
}
```

**81. Implement stack using array.**
```java
class Stack {
    int[] arr;
    int top = -1;
    public void push(int val) {
        if(top == arr.length - 1) throw new RuntimeException("Stack Overflow");
        arr[++top] = val;
    }
    public int pop() {
        if(top == -1) throw new RuntimeException("Stack Empty");
        return arr[top--];
    }
}
```

**82. Check balanced parentheses.**
```java
public boolean isValid(String s) {
    Stack<Character> stack = new Stack<>();
    for(char c : s.toCharArray()) {
        if(c == '(' || c == '{' || c == '[') stack.push(c);
        else {
            if(stack.isEmpty()) return false;
            char top = stack.pop();
            if(c == ')' && top != '(') return false;
            if(c == '}' && top != '{') return false;
            if(c == ']' && top != '[') return false;
        }
    }
    return stack.isEmpty();
}
```

**83. Find first non-repeating character.**
```java
public char firstNonRepeating(String s) {
    Map<Character, Integer> count = new HashMap<>();
    for(char c : s.toCharArray()) {
        count.put(c, count.getOrDefault(c, 0) + 1);
    }
    for(char c : s.toCharArray()) {
        if(count.get(c) == 1) return c;
    }
    return '\0';
}
```

**84. Two sum problem.**
```java
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for(int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if(map.containsKey(complement)) {
            return new int[]{map.get(complement), i};
        }
        map.put(nums[i], i);
    }
    return new int[]{};
}
```

**85. Binary search implementation.**
```java
public int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;
    while(left <= right) {
        int mid = left + (right - left) / 2;
        if(arr[mid] == target) return mid;
        if(arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```

**86. Merge two sorted arrays.**
```java
public int[] merge(int[] a, int[] b) {
    int[] result = new int[a.length + b.length];
    int i = 0, j = 0, k = 0;
    while(i < a.length && j < b.length) {
        if(a[i] <= b[j]) result[k++] = a[i++];
        else result[k++] = b[j++];
    }
    while(i < a.length) result[k++] = a[i++];
    while(j < b.length) result[k++] = b[j++];
    return result;
}
```

**87. Find factorial using recursion.**
```java
public int factorial(int n) {
    if(n <= 1) return 1;
    return n * factorial(n - 1);
}
```

**88. Explain time complexities with examples.**
| Complexity | Name | Example |
|------------|------|---------|
| O(1) | Constant | Array access |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Single loop |
| O(n²) | Quadratic | Nested loops |

---

## Git & Maven

**89. Explain Git workflow - add, commit, push, pull, merge.**
```bash
git add .                    # Stage changes
git commit -m "Message"      # Commit changes
git push origin main         # Push to remote
git pull origin main         # Pull from remote
git merge feature-branch     # Merge branch
```

**90. Branching strategy explanation.**
```
main (production)
  └── develop (development)
      ├── feature/user-auth
      ├── feature/payment
      └── release/v1.0
          └── hotfix/bug-123
```

**91. What is pom.xml structure?**
```xml
<project>
    <groupId>com.company</groupId>
    <artifactId>app-name</artifactId>
    <version>1.0.0</version>
    
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
    
    <properties>
        <java.version>17</java.version>
    </properties>
</project>
```

**92. Maven lifecycle phases.**
- **compile**: Compile source code
- **test**: Run tests
- **package**: Create JAR/WAR
- **install**: Install to local repository
- **deploy**: Deploy to remote repository

---

# 📌 PROJECT-BASED QUESTIONS (Most Important for Interviews)

## Employee Management System
**93. How to map Employee and Department relationship?**
```java
@Entity
public class Department {
    @OneToMany(mappedBy = "department")
    private List<Employee> employees;
}

@Entity
public class Employee {
    @ManyToOne
    @JoinColumn(name = "dept_id")
    private Department department;
}
```

**94. How to search employees by name, department, salary?**
```java
@Repository
public interface EmployeeRepository extends JpaRepository<Employee, Long> {
    List<Employee> findByNameContaining(String name);
    List<Employee> findByDepartmentName(String deptName);
    List<Employee> findBySalaryBetween(Double min, Double max);
    
    @Query("SELECT e FROM Employee e WHERE e.name LIKE %:name% AND e.department.name = :dept")
    List<Employee> search(@Param("name") String name, @Param("dept") String dept);
}
```

**95. How to implement pagination and sorting?**
```java
@GetMapping("/employees")
public Page<Employee> getAll(
    @RequestParam(defaultValue = "0") int page,
    @RequestParam(defaultValue = "10") int size,
    @RequestParam(defaultValue = "id") String sortBy,
    @RequestParam(defaultValue = "asc") String direction
) {
    Sort sort = direction.equals("asc") ? Sort.by(sortBy).ascending() : Sort.by(sortBy).descending();
    Pageable pageable = PageRequest.of(page, size, sort);
    return employeeRepository.findAll(pageable);
}
```

---

## Library Management System
**96. How to implement book issue/return logic?**
```java
@Service
@Transactional
public class BookService {
    public void issueBook(Long bookId, Long memberId) {
        Book book = bookRepository.findById(bookId).orElseThrow();
        if(!book.isAvailable()) throw new BookNotAvailableException();
        
        Transaction transaction = new Transaction();
        transaction.setBook(book);
        transaction.setMember(member);
        transaction.setIssueDate(LocalDate.now());
        transaction.setDueDate(LocalDate.now().plusDays(14));
        transaction.setStatus(Status.ISSUED);
        
        book.setAvailable(false);
        transactionRepository.save(transaction);
    }
    
    public void returnBook(Long transactionId) {
        Transaction transaction = transactionRepository.findById(transactionId).orElseThrow();
        transaction.setReturnDate(LocalDate.now());
        transaction.setStatus(Status.RETURNED);
        
        if(LocalDate.now().isAfter(transaction.getDueDate())) {
            long daysLate = ChronoUnit.DAYS.between(transaction.getDueDate(), LocalDate.now());
            double fine = daysLate * 10.0; // Rs.10 per day
            transaction.setFine(fine);
        }
        
        Book book = transaction.getBook();
        book.setAvailable(true);
        transactionRepository.save(transaction);
    }
}
```

---

## WorkNest (Resume Project - Most Important)

**97. How did you implement JWT authentication?**
```java
@Component
public class JwtTokenProvider {
    private String jwtSecret = "secretKey";
    private int jwtExpiration = 86400000; // 24 hours
    
    public String generateToken(Authentication authentication) {
        UserPrincipal user = (UserPrincipal) authentication.getPrincipal();
        Date now = new Date();
        Date expiryDate = new Date(now.getTime() + jwtExpiration);
        
        return Jwts.builder()
            .setSubject(user.getUsername())
            .setIssuedAt(now)
            .setExpiration(expiryDate)
            .signWith(SignatureAlgorithm.HS512, jwtSecret)
            .compact();
    }
    
    public boolean validateToken(String token) {
        try {
            Jwts.parser().setSigningKey(jwtSecret).parseClaimsJws(token);
            return true;
        } catch (JwtException | IllegalArgumentException e) {
            return false;
        }
    }
}
```

**98. How did you handle role-based access?**
```java
@Entity
public class User {
    @Enumerated(EnumType.STRING)
    private Role role;
}

public enum Role {
    ROLE_ADMIN,
    ROLE_MANAGER,
    ROLE_USER
}

@RestController
@RequestMapping("/api/workspace")
public class WorkspaceController {
    
    @PreAuthorize("hasRole('ADMIN') or hasRole('MANAGER')")
    @PostMapping
    public Workspace createWorkspace(@RequestBody Workspace workspace) {
        return workspaceService.create(workspace);
    }
    
    @PreAuthorize("hasRole('ADMIN')")
    @DeleteMapping("/{id}")
    public void deleteWorkspace(@PathVariable Long id) {
        workspaceService.delete(id);
    }
}
```

**99. How did you map Task and Workspace relationships?**
```java
@Entity
public class Workspace {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String name;
    
    @OneToMany(mappedBy = "workspace", cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    private List<Task> tasks;
    
    @ManyToOne
    @JoinColumn(name = "owner_id")
    private User owner;
    
    @ManyToMany
    @JoinTable(
        name = "workspace_members",
        joinColumns = @JoinColumn(name = "workspace_id"),
        inverseJoinColumns = @JoinColumn(name = "member_id")
    )
    private Set<User> members = new HashSet<>();
}

@Entity
public class Task {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String title;
    private String description;
    private TaskStatus status;
    private LocalDateTime dueDate;
    
    @ManyToOne
    @JoinColumn(name = "workspace_id")
    private Workspace workspace;
    
    @ManyToOne
    @JoinColumn(name = "assigned_to")
    private User assignedTo;
}
```

**100. How did you implement global exception handling?**
```java
@ControllerAdvice
public class GlobalExceptionHandler {
    
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleNotFound(ResourceNotFoundException ex) {
        ErrorResponse error = new ErrorResponse(
            HttpStatus.NOT_FOUND.value(),
            ex.getMessage(),
            LocalDateTime.now()
        );
        return ResponseEntity.status(HttpStatus.NOT_FOUND).body(error);
    }
    
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<ErrorResponse> handleValidation(MethodArgumentNotValidException ex) {
        List<String> errors = ex.getBindingResult()
            .getAllErrors()
            .stream()
            .map(DefaultMessageSourceResolvable::getDefaultMessage)
            .collect(Collectors.toList());
        
        ErrorResponse error = new ErrorResponse(
            HttpStatus.BAD_REQUEST.value(),
            "Validation failed: " + String.join(", ", errors),
            LocalDateTime.now()
        );
        return ResponseEntity.badRequest().body(error);
    }
    
    @ExceptionHandler(AccessDeniedException.class)
    public ResponseEntity<ErrorResponse> handleAccessDenied(AccessDeniedException ex) {
        ErrorResponse error = new ErrorResponse(
            HttpStatus.FORBIDDEN.value(),
            "Access denied",
            LocalDateTime.now()
        );
        return ResponseEntity.status(HttpStatus.FORBIDDEN).body(error);
    }
}
```

**101. What is your database schema design?**
```sql
-- Users
CREATE TABLE users (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Workspaces
CREATE TABLE workspaces (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    owner_id BIGINT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (owner_id) REFERENCES users(id)
);

-- Workspace Members (Many-to-Many)
CREATE TABLE workspace_members (
    workspace_id BIGINT,
    member_id BIGINT,
    PRIMARY KEY (workspace_id, member_id),
    FOREIGN KEY (workspace_id) REFERENCES workspaces(id),
    FOREIGN KEY (member_id) REFERENCES users(id)
);

-- Tasks
CREATE TABLE tasks (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(200) NOT NULL,
    description TEXT,
    status VARCHAR(20),
    due_date TIMESTAMP,
    workspace_id BIGINT,
    assigned_to BIGINT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (workspace_id) REFERENCES workspaces(id),
    FOREIGN KEY (assigned_to) REFERENCES users(id)
);
```

**102. List your REST APIs with endpoints.**
```
Authentication APIs:
POST   /api/auth/login           - Login user
POST   /api/auth/register        - Register user
POST   /api/auth/logout          - Logout

Workspace APIs:
GET    /api/workspaces           - Get all workspaces
POST   /api/workspaces           - Create workspace
GET    /api/workspaces/{id}      - Get workspace details
PUT    /api/workspaces/{id}      - Update workspace
DELETE /api/workspaces/{id}      - Delete workspace
POST   /api/workspaces/{id}/members - Add member
DELETE /api/workspaces/{id}/members/{userId} - Remove member

Task APIs:
GET    /api/workspaces/{id}/tasks - Get all tasks
POST   /api/workspaces/{id}/tasks - Create task
GET    /api/tasks/{id}           - Get task details
PUT    /api/tasks/{id}           - Update task
DELETE /api/tasks/{id}           - Delete task
PATCH  /api/tasks/{id}/status    - Update task status
POST   /api/tasks/{id}/assign    - Assign task
```

**103. How did you implement security?**
```java
@Configuration
@EnableWebSecurity
@EnableGlobalMethodSecurity(prePostEnabled = true)
public class SecurityConfig {
    
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            .csrf().disable()
            .cors().disable()
            .sessionManagement().sessionCreationPolicy(SessionCreationPolicy.STATELESS)
            .and()
            .authorizeHttpRequests(authz -> authz
                .requestMatchers("/api/auth/**").permitAll()
                .requestMatchers("/api/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            )
            .oauth2ResourceServer()
            .jwt();
        
        return http.build();
    }
    
    @Bean
    public AuthenticationManager authenticationManager(AuthenticationConfiguration config) 
            throws Exception {
        return config.getAuthenticationManager();
    }
    
    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

**104. How did you integrate with Angular frontend?**
- **CORS**: Configured to allow Angular origin
- **API**: REST endpoints returning JSON
- **Authentication**: JWT token in Authorization header
- **Communication**: HttpClient in Angular
- **State**: Using localStorage for token storage
```java
@Configuration
public class CorsConfig {
    @Bean
    public WebMvcConfigurer corsConfigurer() {
        return new WebMvcConfigurer() {
            @Override
            public void addCorsMappings(CorsRegistry registry) {
                registry.addMapping("/api/**")
                    .allowedOrigins("http://localhost:4200")
                    .allowedMethods("*")
                    .allowedHeaders("*")
                    .allowCredentials(true);
            }
        };
    }
}
```

**105. Where did you deploy?**
- **AWS EC2** / **Azure VM** / **Heroku** (choose based on what you know)
- **Database**: AWS RDS / PostgreSQL on VM
- **CI/CD**: GitHub Actions or Jenkins
- **Container**: Docker (if you know)

---

# 🎯 TOP 50 INTERVIEW QUESTIONS FOR FRESHER

1. Java features
2. OOP principles (4 pillars)
3. Exception handling types
4. Collections hierarchy
5. HashMap internal working
6. ArrayList vs LinkedList
7. Multithreading vs multitasking
8. Spring Boot vs Spring
9. REST API principles
10. SQL joins with examples
11. JPA relationships
12. JWT authentication flow
13. DSA basics (2-3 problems)
14. Project explanation with challenges
15. Agile methodology
16. SDLC phases
17. Git workflow
18. Maven lifecycle
19. Dependency Injection
20. @Transactional annotation
21. Lazy vs Eager loading
22. N+1 problem solution
23. Global exception handling
24. Validation in Spring
25. @PathVariable vs @RequestParam
26. HTTP status codes
27. DTO vs Entity
28. Optional class usage
29. Lambda expressions
30. Stream API
31. Functional interfaces
32. Checked vs Unchecked exceptions
33. final, finally, finalize
34. String immutability
35. Constructor chaining
36. Abstract class vs Interface
37. Singleton pattern
38. Factory pattern
39. SOLID principles
40. ACID properties
41. Normalization
42. Index performance
43. Transaction management
44. Deadlock prevention
45. Thread pool
46. ExecutorService
47. Synchronized keyword
48. Volatile keyword
49. Spring Security flow
50. Your project - WorkNest

---

# 🔥 DAILY PRACTICE SCHEDULE

| Time | Activity | Focus |
|------|----------|-------|
| 2 hours | DSA Problems | 2-3 LeetCode problems |
| 2 hours | Core Concepts | Spring Boot + Java |
| 1 hour | SQL Practice | Complex queries |
| 1 hour | Project Development | Building WorkNest |

---

# 📚 RECOMMENDED RESOURCES

**YouTube Channels:**
- CodeWithHarry (Hindi/English)
- Telusko
- Java Brains
- Amigoscode

**Practice Platforms:**
- LeetCode (Easy + Medium)
- HackerRank
- SQLZoo
- W3Schools

**GitHub:**
- Search "Spring Boot projects"
- Search "Spring Security JWT example"

---

This comprehensive question bank covers ALL topics. Practice these concepts, build 2-3 projects, and you'll be ready for Java Backend Developer fresher roles in 5 months! 🚀

**Remember**: Focus on understanding concepts, not memorizing answers. Good luck! 💪

*Need detailed explanation for any topic? Just ask!*

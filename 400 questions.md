# Complete Java Backend Developer Interview Questions List

---

## MONTH 1: CORE JAVA

### Variables, Data Types & Operators
1. What's the difference between primitive and non-primitive data types?
2. What are the types of type casting? Explain implicit vs explicit.
3. What's the difference between `==` and `.equals()`?
4. Difference between logical operators (&&, ||) and bitwise operators (&, |)?
5. What's the output of `System.out.println(10 + 20 + "Hello")`? Why?
6. What's the output of `System.out.println("Hello" + 10 + 20)`? Why?
7. What is type promotion in expressions?
8. Explain variable scoping in Java.
9. What are wrapper classes? Why do we need them?
10. What is autoboxing and unboxing?

### Control Statements & Arrays
11. Why use `break` in switch statement? What is fall-through?
12. When to use for-each loop? What are limitations?
13. How is 2D array stored in memory?
14. Why does ArrayIndexOutOfBoundsException occur? How to avoid?
15. What is the difference between `break` and `continue`?
16. Can we use `switch` with strings? (Java 7+)
17. What are enhanced for loops vs traditional for loops?
18. How to copy arrays efficiently?
19. What is jagged array?
20. How to convert array to ArrayList and vice versa?

### Methods & OOP Basics
21. How to achieve method overloading? Can we change return type?
22. What is constructor chaining? How to use `this()` and `super()`?
23. How to achieve encapsulation? Give example.
24. Why doesn't Java support multiple inheritance? How do interfaces solve it?
25. Difference between abstract class and interface? When to use what?
26. Explain access modifiers with scope.
27. What is method overriding? Rules for overriding?
28. Can we override static methods? Why?
29. What is final keyword? Where can we use it?
30. What is the difference between composition and aggregation?
31. What is static block and instance block?
32. Can we have a private constructor? What is the use?
33. What is the Object class and its methods?
34. What is shallow copy and deep copy?
35. What is polymorphism? Runtime vs Compile-time?

### String & Exception Handling
36. Why is String immutable? What are benefits?
37. Difference between String, StringBuilder, StringBuffer? Performance comparison?
38. What's the flow of `try-catch-finally`? When doesn't finally execute?
39. Difference between Checked and Unchecked exceptions? Give examples.
40. How to create custom exception? Difference between `throw` and `throws`?
41. What is try-with-resources?
42. What is the difference between Exception and Error?
43. Can we have try without catch?
44. What is multi-catch block? (Java 7+)
45. What are the methods of the Throwable class?
46. What is the use of `finalize()` method?
47. String pool concept - what and why?
48. What is string interning?
49. What are the different ways to create String objects?
50. When to use StringBuilder vs StringBuffer?

---

## MONTH 2: COLLECTIONS + MULTITHREADING + SQL

### Collections Framework
51. ArrayList vs LinkedList - performance comparison? When to use what?
52. How does HashMap work internally? Role of equals() and hashCode()?
53. How does HashSet detect duplicates?
54. TreeMap vs HashMap - difference? How does sorting work?
55. Comparable vs Comparator - difference? Real example?
56. Why does ConcurrentModificationException occur? Solution?
57. What is the difference between Collection and Collections?
58. What is fail-fast and fail-safe iterators?
59. What is BlockingQueue? When to use?
60. What are the differences between HashMap and Hashtable?
61. What is ConcurrentHashMap? How does it differ from HashMap?
62. What is LinkedHashMap? When to use?
63. What is TreeSet vs HashSet?
64. What is PriorityQueue? How does it work?
65. What is the difference between Iterator and ListIterator?
66. What is EnumSet and EnumMap?
67. What is WeakHashMap? When to use?
68. What is IdentityHashMap?
69. How does ArrayList increase its size dynamically?
70. What is the initial capacity of HashMap and load factor?

### Multithreading
71. Thread class vs Runnable interface - which is better and why?
72. What are thread lifecycle states?
73. Why need synchronization? How does synchronized keyword work?
74. What is deadlock? Give example and how to avoid?
75. What are benefits of ExecutorService over Thread class?
76. Callable vs Runnable - difference? What is Future?
77. What is the difference between `sleep()` and `wait()`?
78. What is the difference between `notify()` and `notifyAll()`?
79. What is volatile keyword? When to use?
80. What is the difference between synchronized method and block?
81. What is ThreadLocal? When to use?
82. What is CountDownLatch? When to use?
83. What is CyclicBarrier? When to use?
84. What is Semaphore? When to use?
85. What is the difference between process and thread?
86. What is context switching?
87. What is a daemon thread?
88. What is the difference between interrupt and stop?
89. What is the use of `join()` method?
90. What is the difference between `yield()` and `sleep()`?

### Java 8 Features
91. What is Lambda expression? How related to Functional Interface?
92. What is Stream API? Use of map(), filter(), reduce()?
93. Why use Optional? How does it prevent NullPointerException?
94. What is method reference? Types?
95. What is default method in interface? Why needed?
96. What is static method in interface?
97. What is the difference between Stream and Collection?
98. What are intermediate and terminal operations in Stream?
99. What is parallel stream? When to use?
100. What is the difference between findFirst() and findAny()?
101. What is flatMap() in Stream?
102. What are the functional interfaces in Java 8?
103. What is Predicate, Function, Consumer, Supplier?
104. What is the difference between map() and flatMap()?
105. What is the use of Collectors class?

### SQL
106. Explain SQL joins with examples - INNER, LEFT, RIGHT, FULL?
107. GROUP BY vs ORDER BY - difference?
108. HAVING vs WHERE - when to use what?
109. Subquery vs Join - which is better and why?
110. What is Index? Types and benefits? Performance impact?
111. What is Normalization? Explain 1NF, 2NF, 3NF?
112. What is the difference between DELETE, TRUNCATE, and DROP?
113. What is the difference between UNION and UNION ALL?
114. What is the difference between primary key and unique key?
115. What is foreign key constraint?
116. What are aggregate functions?
117. What is the difference between WHERE and HAVING?
118. What is a self join? Give example.
119. What is the difference between correlated and non-correlated subquery?
120. What is ACID properties?
121. What is the difference between view and table?
122. What is a stored procedure? Benefits?
123. What is the difference between function and stored procedure?
124. What is a trigger in SQL?
125. What is the difference between cluster and non-cluster index?
126. What is the use of NVL, COALESCE, ISNULL functions?
127. What is the difference between RANK, DENSE_RANK, and ROW_NUMBER?
128. What is the difference between IN and EXISTS?
129. What is the difference between BETWEEN and IN?
130. What is the use of the LIKE operator?

---

## MONTH 3: JDBC + SPRING CORE + SPRING BOOT

### JDBC
131. What are JDBC steps from connection to data fetch?
132. Statement vs PreparedStatement - which is better and why?
133. What is SQL Injection? How does PreparedStatement prevent it?
134. Transaction management in JDBC? commit() and rollback()?
135. What is the difference between execute, executeQuery, and executeUpdate?
136. What is DataSource? Why use it over DriverManager?
137. What is Connection Pooling? Why needed?
138. What is the difference between ResultSet types?
139. What is RowSet? When to use?
140. How to handle BLOB and CLOB in JDBC?
141. What is the difference between JDBC and JPA?
142. What are batch updates in JDBC? Benefits?
143. What is the use of setAutoCommit(false)?
144. How to call stored procedures using JDBC?
145. What is ResultSetMetaData and DatabaseMetaData?
146. What is the difference between Type 1, 2, 3, 4 JDBC drivers?
147. What is the best practice for closing JDBC resources?
148. What is the difference between Statement and CallableStatement?
149. How to handle large result sets efficiently?
150. What is the difference between scrollable and forward-only ResultSet?

### Spring Core
151. What is IoC (Inversion of Control)? How implemented in Spring?
152. Types of Dependency Injection?
153. Difference between `@Component`, `@Service`, `@Repository`, `@Controller`?
154. What are bean scopes in Spring?
155. How does `@Autowired` work? When to use `@Qualifier`?
156. What is the difference between BeanFactory and ApplicationContext?
157. What is the purpose of @Configuration and @Bean?
158. What is component scanning? How to configure?
159. What is the difference between @Component and @Bean?
160. What is the lifecycle of a Spring Bean?
161. What is the use of @Value annotation?
162. What is the difference between @Primary and @Qualifier?
163. What is the @PostConstruct and @PreDestroy annotation?
164. What is the difference between Singleton and Prototype scope?
165. What is AOP? Where to use it?
166. What is the difference between @Before, @After, @Around, @AfterReturning, @AfterThrowing?
167. What is the use of @Async annotation?
168. What is the difference between @Transactional and @Cacheable?
169. What is the use of @EventListener?
170. What is the difference between @Import and @ImportResource?
171. What is the use of @Lazy annotation?
172. What is the difference between @Scope and @Lazy?
173. What is the purpose of @Order annotation?
174. What is the difference between @ComponentScan and @EnableAutoConfiguration?
175. What is the use of @PropertySource?

### Spring Boot
176. How does Spring Boot auto-configuration work?
177. application.properties vs application.yml - difference?
178. Spring Boot layered architecture explain.
179. `@RestController` vs `@Controller` - difference?
180. How to implement validation?
181. How to handle global exceptions?
182. What is Spring Boot Starter? Why needed?
183. What is the difference between Spring and Spring Boot?
184. What is the purpose of @SpringBootApplication?
185. How to change the default port in Spring Boot?
186. What is the use of spring-boot-devtools?
187. What is Actuator in Spring Boot? What endpoints it provides?
188. What is the difference between @RequestMapping and @GetMapping?
189. What is the use of @PathVariable and @RequestParam?
190. How to handle file upload in Spring Boot?
191. What is the use of @ResponseBody and @RequestBody?
192. What is the difference between @ResponseStatus and ResponseEntity?
193. How to configure multiple datasources in Spring Boot?
194. What is Spring Boot Profiles? How to use?
195. What is the difference between @Profile and @Conditional?
196. How to create a custom starter in Spring Boot?
197. What is the use of @EnableAutoConfiguration?
198. What is the difference between @ConditionalOnClass and @ConditionalOnMissingBean?
199. How to implement caching in Spring Boot?
200. What is the use of @Scheduled annotation?

---

## MONTH 4: REST API + JPA + SECURITY

### REST API
201. What are REST API principles?
202. `@RequestMapping` vs `@GetMapping` - difference?
203. `@PathVariable` vs `@RequestParam` - when to use?
204. Why use ResponseEntity? Benefits?
205. What is DTO? Why use it? Separate from Entity?
206. Explain HTTP status codes.
207. What is the difference between PUT and PATCH?
208. What is the difference between POST and PUT?
209. What is the difference between REST and SOAP?
210. What is HATEOAS? Why needed?
211. What is Swagger/OpenAPI? How to implement?
212. What is the difference between @RequestBody and @ModelAttribute?
213. What is Content Negotiation in REST?
214. What are the best practices for REST API design?
215. What is the difference between RESTful and REST API?
216. What is API versioning? How to implement?
217. What is the use of @ResponseStatus?
218. How to handle JSON serialization/deserialization?
219. What is the difference between @JsonIgnore and @JsonManagedReference?
220. What is the use of @JsonFormat?
221. What is the difference between application/json and application/xml?
222. What is the use of @Validated?
223. What is the difference between @Min, @Max, @Size, @Pattern?
224. How to create custom validation annotation?
225. What is the use of @RestControllerAdvice?
226. What is the difference between @ExceptionHandler and @ControllerAdvice?
227. How to handle validation exceptions globally?
228. What is the difference between 400 and 422 status codes?
229. How to implement pagination in REST API?
230. How to implement sorting in REST API?

### JPA/Hibernate
231. JPA vs Hibernate - difference? What is ORM?
232. How to map entity relationships?
233. Lazy vs Eager loading - difference? Performance impact?
234. What is N+1 query problem? Solution?
235. JPQL vs Native SQL - which is better?
236. How to implement pagination?
237. What is EntityManager? Difference from Hibernate Session?
238. What is the difference between @Entity and @Table?
239. What is the difference between @Id and @GeneratedValue?
240. What are the different generation strategies?
241. What is the difference between CascadeType and FetchType?
242. What is the difference between @OneToMany and @ManyToMany?
243. What is the use of @JoinColumn and @JoinTable?
244. What is the difference between @Column and @JoinColumn?
245. What is the purpose of @Transient?
246. What is the difference between persist() and save()?
247. What is the difference between get() and load()?
248. What is the difference between update() and merge()?
249. What is the difference between flush() and commit()?
250. What is the first-level cache and second-level cache?
251. How to enable query caching in Hibernate?
252. What is the use of @NamedQuery and @NamedNativeQuery?
253. What is the difference between JPA Criteria API and JPQL?
254. What is the use of @MappedSuperclass?
255. How to implement soft delete using JPA?
256. What is the difference between @Version and @OptimisticLock?
257. What is the difference between Entity Lifecycle and Callback methods?
258. What is the use of @PostPersist, @PrePersist, @PostLoad?
259. What is the difference between JpaRepository and CrudRepository?
260. What is the use of @Query annotation?

### Spring Security
261. Authentication vs Authorization - difference?
262. What is BCryptPasswordEncoder? How to store passwords?
263. What is JWT structure? Header, Payload, Signature?
264. Explain JWT authentication flow.
265. How to implement role-based access?
266. How does Spring Security filter chain work?
267. What is the difference between @PreAuthorize and @RolesAllowed?
268. What is the use of SecurityContextHolder?
269. How to implement custom AuthenticationProvider?
270. What is the difference between UserDetails and UserDetailsService?
271. How to implement logout in Spring Security?
272. What is the difference between formLogin and oauth2Login?
273. What is the use of @EnableWebSecurity?
274. What is the difference between hasRole and hasAuthority?
275. How to implement method-level security?
276. What is the difference between permitAll and anonymous?
277. What is the use of @AuthenticationPrincipal?
278. How to configure CORS in Spring Security?
279. What is the difference between Basic Auth and JWT?
280. How to store JWT securely?
281. What is the difference between access token and refresh token?
282. How to implement token refresh mechanism?
283. What is the use of @EnableGlobalMethodSecurity?
284. What is the difference between hasPermission and hasRole?
285. How to implement OAuth2 in Spring Boot?
286. What is the use of SecurityConfigurerAdapter?
287. How to handle session management in Spring Security?
288. What is the difference between session and JWT?
289. How to implement multi-factor authentication?
290. What are the best practices for Spring Security?

---

## MONTH 5: DSA + GIT + PROJECTS

### DSA Questions
291. Find missing number in array (1 to n).
292. Reverse a string without inbuilt function.
293. Find duplicate elements in array.
294. Check if string is palindrome.
295. Find middle element of linked list in single pass.
296. Implement stack using array.
297. Check balanced parentheses.
298. Find first non-repeating character.
299. Two sum problem.
300. Binary search implementation.
301. Merge two sorted arrays.
302. Find factorial using recursion.
303. Explain time complexities with examples.
304. Reverse a linked list.
305. Find maximum subarray sum (Kadane's Algorithm).
306. Find the intersection of two arrays.
307. Check if two strings are anagrams.
308. Find the longest common prefix.
309. Remove duplicates from sorted array.
310. Move all zeros to end of array.
311. Find the third largest element in array.
312. Check if a number is prime.
313. Find GCD of two numbers.
314. Implement a queue using two stacks.
315. Find the first occurrence of a substring (KMP).
316. Check if a string contains all unique characters.
317. Find the longest substring without repeating characters.
318. Rotate an array by k positions.
319. Find the peak element in an array.
320. Implement binary tree traversal (inorder, preorder, postorder).
321. Find height of a binary tree.
322. Check if a binary tree is balanced.
323. Find lowest common ancestor in binary tree.
324. Level order traversal of binary tree.
325. Validate binary search tree.

### Git & Maven
326. Explain Git workflow - add, commit, push, pull, merge.
327. Branching strategy explanation.
328. What is pom.xml structure?
329. Maven lifecycle phases.
330. What is the difference between Git and SVN?
331. How to resolve merge conflicts?
332. What is the difference between git merge and git rebase?
333. What is git stash? When to use?
334. What is the difference between git fetch and git pull?
335. What is git cherry-pick?
336. What is the difference between git reset and git revert?
337. What is the use of .gitignore file?
338. What is the difference between git clone and git fork?
339. What is the use of @Profile in Maven?
340. What is the difference between compile, package, and install goals?
341. What is the use of Maven profiles?
342. What is the difference between dependencyManagement and dependencies?
343. What is the use of build plugins in Maven?
344. What is the difference between Maven and Gradle?
345. How to create a multi-module Maven project?
346. What is the use of -DskipTests and -Dmaven.test.skip?
347. How to exclude a transitive dependency in Maven?
348. What is the difference between provided and compile scope?
349. What is the purpose of Maven repository?
350. What is the difference between snapshot and release versions?

---

## INTERVIEW TOP 50 (MUST PRACTICE)

1. Explain OOP principles.
2. Difference between ArrayList and LinkedList.
3. How HashMap works internally.
4. Difference between Checked and Unchecked exceptions.
5. String immutability in Java.
6. Difference between Abstract Class and Interface.
7. JDBC vs JPA/Hibernate.
8. REST API principles.
9. SQL joins explanation.
10. Authentication vs Authorization.
11. JWT authentication flow.
12. Difference between @RestController and @Controller.
13. Spring Boot auto-configuration.
14. Difference between @Component, @Service, @Repository.
15. Why use Optional in Java 8?
16. Lambda expressions and Functional Interfaces.
17. Stream API - map, filter, reduce.
18. Difference between HashMap and ConcurrentHashMap.
19. Exception handling - try-catch-finally.
20. Difference between sleep() and wait().
21. ExecutorService in multithreading.
22. Primary key vs Unique key in SQL.
23. Index in database - types and benefits.
24. N+1 query problem and solution.
25. JPA relationships - OneToMany, ManyToOne.
26. Spring Security filter chain.
27. BCrypt password encoding.
28. Role-based access control.
29. Difference between PUT and PATCH.
30. ResponseEntity usage in REST.
31. DTO vs Entity.
32. Validation in Spring Boot.
33. Global exception handling.
34. Pagination and sorting in JPA.
35. Difference between JPQL and Native SQL.
36. Lazy vs Eager loading.
37. Difference between @RequestParam and @PathVariable.
38. HTTP status codes.
39. Thread lifecycle states.
40. Synchronized keyword usage.
41. Comparable vs Comparator.
42. Finally block execution.
43. Constructor chaining.
44. Access modifiers.
45. Method overloading vs overriding.
46. Git branching strategy.
47. Maven lifecycle.
48. SOLID principles.
49. ACID properties.
50. Your project explanation - WorkNest.

---

## PROJECT-SPECIFIC QUESTIONS

### Employee Management System
- How to map Employee and Department relationship?
- How to search employees by name, department, salary?
- How to implement pagination and sorting?
- How to handle employee leave management?

### Library Management System
- How to implement book issue/return logic?
- How to calculate fine for late returns?
- How to handle book reservations?
- How to implement search by author, genre, year?

### WorkNest (Resume Project - Most Important)
- How did you implement JWT authentication?
- How did you handle role-based access?
- How did you map Task and Workspace relationships?
- How did you implement global exception handling?
- What is your database schema design?
- List your REST APIs with endpoints.
- How did you implement security?
- How did you integrate with Angular frontend?
- Where did you deploy?
- What were the major challenges and how did you solve them?
- How did you handle concurrent task updates?
- How did you implement workspace member management?
- What design patterns did you use?
- How did you ensure code quality?
- How did you handle logging?

---

## SYSTEM DESIGN QUESTIONS (For Senior/Fresher with projects)

- How would you design a URL shortening service?
- How would you design a chat application?
- How would you design an e-commerce platform?
- How would you design a social media feed?
- How would you design a payment processing system?
- How would you design a notification system?
- How would you design a file storage system?
- How would you design a caching system?
- How would you design a rate limiter?
- How would you design a logging system?

---

This is the **complete question bank** covering all topics in your 5-month roadmap. Practice each question thoroughly, and you'll be ready for any Java Backend Developer fresher interview! 🚀

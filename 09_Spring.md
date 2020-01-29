# 기본 흐름

```java
// client의 요청 - @Controller 진입 - 요청에 대한 작업 수행 - 뷰로 데이터 전달

@Controller												// @Controller 이용하여 클래스 생성
public class HomeController {
	@GetMapping({ "/", "/home" })		// view 요청 경로 설정
	public String index() {
		return "index";								// view 리턴
	}
}
```

<img src="https://t1.daumcdn.net/cfile/tistory/99A76A3F5A78CD3E3B" alt="sts" style="zoom:80%;" />





# @ResponseBody

> JSON 형식의 값을 응답할 때 사용하는 annotation

```java
@RestController 
			= @Controller + @Responsebody
```

```java
@Controller
public class Json1Controller {

	@GetMapping("json/map")
	@ResponseBody
	public Map<String, Object> jsonMap(Map<String, Object> map) {
		Map<String, Object> map2 = new HashMap<String, Object>();
		map2.put("key1", "value");
		map2.put("key2", 2324);
		map2.put("key3", true);
		return map2;
	}
```

```java
@RestController
public class Json2Controller {

	@GetMapping("json2/map")
	public Map<String, Object> jsonMap(Map<String, Object> map) {
		Map<String, Object> map2 = new HashMap<String, Object>();
		map2.put("key1", "value");
		map2.put("key2", 2324);
		map2.put("key3", true);
		return map2;
	}
```



# @GetMapping / @RequestMapping

```java
@RestController
public class MethodController {
@GetMapping("req/get")
@RequestMapping(value="req/get", method=RequestMethod.GET) public String get() {
return "GET"; }
@PostMapping("req/post")
@RequestMapping(value="req/post", method=RequestMethod.POST) public String post() {
return "POST"; }
}
```



# @Bean / @Component

> - Spring Bean: 스프링 컨테이너에 의해서 만들어진 "" 자바 객체 ""
>
> - @Bean과 @Component 모두 Bean 생성을 목적으로 함

##### 1. @Bean

- 개발자가 컨트롤이 불가능한 외부 라이브러리들을 Bean으로 등록하고 싶을 때 사용

```java
@Bean
public ObjectMapper objectMapper(){
    return new ObjectMapper();
}
```



##### 2. @Component

- 개발자가 컨트롤이 가능한 경우 Component를 사용

```java
@Component
public class CustomMapper{
    ...
}
```



# @Autowired

> 

```java
@Repository		@Controller		@Service		@Component
```





# Request 요청 처리

##### 1. HttpServeletRequest

> getParameter() 메소드를 활용하여 파라미터 값 가져오기

```java
@GetMapping("req/http")
	public String http(HttpServletRequest request) {

		String name = request.getParameter("name");
		String pageNum = request.getParameter("pageNum");
		return name + ", " + pageNum;
	}
```



##### 2. RequestParam

> 명칭에 맞게 변수를 사용하고, 종류 및 개수 상관없이 사용 가능하기 때문에 간단함
>
> 1:1로 파라미터를 받을 경우에 사용

```java
	@GetMapping("req/param1")
	public String param1(@RequestParam() String key1, @RequestParam("key2") String key2) {
		return key1 + ", " + key2;
	}

// RequestParam()의 괄호를 비워두면 key1이라는 변수가 괄호 속으로 들어감
// http://localhost:8080/req/param1?key1=123&key2=456
// 출력 결과: 123, 456
```

```java
@GetMapping("req/param2")
	public String param2(@RequestParam Map<String, Object> map) {
		return map.toString();
	}

// http://localhost:8080/req/param2?key1=123&key2=456
// 출력 결과: {key1=123, key2=456}
```



##### 3. ModelAttribute

> Model, DTO, VO 등 객체와 연계하여 활용
>
> 도메인이나 오브젝트로 파라미터를 받을 경우에 사용
>
> Model에 있는 변수명만 받기에 변수명을 정확히 입력해 주어야 함

```java
@GetMapping("req/model")
	public String model(@ModelAttribute Member member) {
		return member.toString();
	}

// http://localhost:8080/req/model
// 출력 결과: Member(name=null, userId=null, userPassword=null)
```



# Thymeleaf

- HTML Template (HTML5 문법 기반)
- Contorller에서 View로 넘겨준 Model을 이용하여 데이터 출력

```java
// build.gradle에 해당 코드 추가
dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-thymeleaf'
}

// refresh gradle (프로젝트 우클릭 - Gradle - Refresh All)
```

```java
@GetMapping("userList")
public String userList(Model model) {
    List<Map<String, Object>> userList = new ArrayList<>();
    Map<String, Object> user = null;
  
    user = new HashMap<>();
    user.put("userId", "a");
    user.put("userName", "apple");
    user.put("userAge", 21);
    userList.add(user);
  
    user = new HashMap<>();
    user.put("userId", "b");
    user.put("userName", "banana");
    user.put("userAge", 22);
    userList.add(user);
  
    user = new HashMap<>();
    user.put("userId", "c");
    user.put("userName", "carrot");
    user.put("userAge", 23);
    userList.add(user);
  
    model.addAttribute("userList", userList);
  
    return "userList";
}
```

```html
<!-- templates/userList.html -->

<body>
	<table border="1">
    <tr>
      <td>아이디</td>
      <td>이름</td>
      <td>나이</td>
    </tr>
    <tr th:each="user : ${userList}">
      <td th:text="${user.userId}"></td>
      <td th:text="${user.userName}"></td>
      <td th:text="${user.userAge}"></td>
    </tr>
	</table>
	<hr>
	<th:block th:each="pageNumber : ${#numbers.sequence(1, 10)}">
		<span th:text="${pageNumber}"></span>
	</th:block>
</body>
```





# 기타

##### 1. 단축키

- shift cmd R (파일 찾아서 열기)
- shift cmd F (코드 배열)
- shift cmd O (전체 import)



##### 2. 새 프로젝트

> 새 프로젝트를 시작할 때에는 BoardApplication - 우클릭 - run as - run



##### 3. import

> 세 가지 중 하나를 선택하여 import

- general - existing projects into workspace
- git - projects from git
- grade - existing gradle project
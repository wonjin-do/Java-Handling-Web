# url에 있는 맵핑값 써먹기
```java
@RestController 
@RequestMapping("/test/*")
public class TestController {

  @RequestMapping(value= "/notice/{num}" , method = RequestMethod.GET)
  public int notice(@PathVariable("num") int num ) throws Exception {
	  return num;
  }	
  
```
# JSON과 HttpStatusCode 전송
new ResponseEntity(Collection list, HttpStatusCode HttpStatus)
```java
  @RequestMapping("/membersList2")
  public  ResponseEntity<List<MemberVO>> listMembers2() {
    List<MemberVO> list = new ArrayList<MemberVO>();
    for (int i = 0; i < 10; i++) {
      MemberVO vo = new MemberVO();
      vo.setId("lee" + i);
      vo.setPwd("123"+i);
      vo.setName("�̼���" + i);
        vo.setEmail("lee"+i+"@test.com");
      list.add(vo);
    }
    return new ResponseEntity(list,HttpStatus.INTERNAL_SERVER_ERROR);//JSON과 HttpStatusCode 전송
  }	
````

# 전송할 데이터 종류와 한글 인코딩 설정
new ResponseEntity(String str, HttpHeaders responseHeaders,HttpStatusCode HttpStatus)
```java
	@RequestMapping(value = "/res3")
	public ResponseEntity res3() {
		HttpHeaders responseHeaders = new HttpHeaders();
	    responseHeaders.add("Content-Type", "text/html; charset=utf-8");
	    String message = "<script>";
		message += " alert('�� ȸ���� ����մϴ�.');";
		message += " location.href='/pro29/test/membersList2'; ";
		message += " </script>";
		return  new ResponseEntity(message, responseHeaders, HttpStatus.CREATED);
	}
	
}
```

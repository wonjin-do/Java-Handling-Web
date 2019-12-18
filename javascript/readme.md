# 제이쿼리
<script  src="http://code.jquery.com/jquery-2.2.1.min.js"></script>

# DOM 생성이후 호출
## DOM생성이후 리소스(이미지, 동영상)의 로딩 완료와 상관없이 진행된다.
```javascript
$(document).ready(function(){				
  
});
```
```javascript
 $(function() {
           
 });
```
## DOM생성이후 리소스전부 다운받은 다음에 진행
```javascript
window.onload = function(){};
```

<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%">$(<span style="color:#4be6fa">document</span>).ready(<span style="color:#ff3399">function</span>(){});</div><div style="padding:0 6px; white-space:pre; line-height:130%">$(<span style="color:#ff3399">function</span>(){});</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

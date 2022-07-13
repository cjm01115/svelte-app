<script>
import Cookies from 'js-cookie'
const urlParams = new URLSearchParams(window.location.search);
let passwd = urlParams.get('passwd');


function api(){
    var url = "https://ko.wikipedia.org/wiki/%EC%98%A4%ED%94%88_API";

    var xhr = new XMLHttpRequest();
    xhr.open("GET", url);

    xhr.onreadystatechange = function () {
    if (xhr.readyState === 4) {
        console.log("cors....")
        console.log(xhr.status);
        console.log(xhr.responseText);
    }};

    xhr.send();
}

if(urlParams.get('passwd')){
    checkPasswd()
}
if(Cookies.get('user')){
    alert("welcome");
    api()
}
function checkPasswd(){
    if(passwd==="1234"){
        alert("welcome");
        Cookies.set('user', Math.random().toString(36));
        api()
    }else{
        alert("word is not correct");
    }
}
const onKeyPress = e => {
    if (e.charCode === 13) (checkPasswd());
  };
</script>

<main>
<p>비밀번호는 1234입니다.</p>
<form action="">
    <input type="password" name="passwd" placeholder="비밀번호를 입력하세요" value={passwd}>
    <input type="submit" value="확인" on:keypress={onKeyPress}>
</form>
</main>

<style>

</style>
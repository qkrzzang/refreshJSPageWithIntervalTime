# refreshJSPageWithIntervalTime
[javascript]intervaltime 값 변경에 따라 화면 html 화면이 intervaltime 후 refresh

$(refreshButton)[0].text는 숫자 값 
 - 5 / 10 / 30

<pre><code>
let makeInterval;
let intervalTime=null;
let intervalId;

$(document).ready(function() {

  $('.interval-button').find('a').on('click', changeRefreshTime);
  // 화면 refresh
  makeInterval = duration => {
    intervalId = setInterval(waitFunction, duration);
  };

  if (intervalTime == null) {
    intervalTime = 1000 * 60 * 5; // 5분 기본셋팅
    waitFunction();
  }

});

function changeRefreshTime(e) {
  let refreshButton = e.currentTarget;
  let refreshTime = Number($(refreshButton)[0].text) * 1000;
  intervalTime = refreshTime

  waitFunction(refreshTime);
}

function waitFunction() {
  clearInterval(intervalId);
  //console.log('intervalTime = ' + intervalTime);
  makeInterval(intervalTime);
}
</code></pre>

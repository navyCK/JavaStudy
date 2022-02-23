### 일반 데이터 전송
```java
normal.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        JsonGetter webGetter = new JsonGetter();
        // 새로운 json을 받겠다는 것. 자주 쓰는 방법으로 3가지가 있는데
        // 1. public JsonGetter() - 일반적인 방법이다.
        // 2. public JsonGetter(boolean useMultipart) - 멀티 파트가 true이면 파일 전송을 한다.
        // 3. public JsonGetter(CookieData cookieData) - 쿠키 데이터까지 전송한다.
            
        ArrayList<NameValuePair> parameters = new ArrayList<>();
        parameters.add(new NameValuePair("name", "value!#&=$Test뷁1"+System.currentTimeMillis()));
        parameters.add(new NameValuePair("name", "valueTest뷁2"));
        // 데이터 타입 NameValuePair로 받아서 ArrayList 생성 후 파라미터 추가
        // 여기서는 NameValuePair(String name, String value)으로만 받기로 했다.
        
        
        webGetter.execute(new OnGetterListener() {
            @Override
            public void onSuccess(String responseTime, String resultCode, JsonObject json) {
                Log.e("CHECK", "responseTime: "+responseTime);
                Log.e("CHECK", "resultCode: "+resultCode);
                Log.e("CHECK", "json: "+json);
            }

            @Override
            public void onError(boolean networkFail, boolean invalidJson, boolean invalidHLJson, String rawJson) {
                if(networkFail)
                    Log.e("CHECK", "통신에 문제가 있습니다.");
                if(invalidJson)
                    Log.e("CHECK", "JSON 형식에 맞지 않습니다.");
                if(invalidHLJson)
                    Log.e("CHECK", "허브링커 JSON 형식에 맞지 않습니다.");
                if(rawJson!=null)
                    Log.e("CHECK", rawJson);
            }

            @Override
            public boolean onComplete(int code) {
                return false;
            }
        }, "http://localhost/webTest/maker.jsp", parameters);
        // excute - 실행에도 여러가지 메소드가 존재하는데, 여기서는
        // public void execute(OnGetterListener onGetterListener, String urlAddr, List<NameValuePair> parameters)
        // 의 방법으로 실행하는 모습이다. 1. 해당 리스너를 사용하여 2. 이 url에 3. parameters를 전송하는 방식이다.
    }
});
```

# 基于okhttp框架的封装。

1. Get 同步请求

		 try {
            Response response = OkHttpClientManager.getAsyn("url");
            String string = response.body().string();
        } catch (IOException e) {
            e.printStackTrace();
        }

2. Get 异步请求

		 OkHttpClientManager.getAsyn("url", new OkHttpClientManager.StringCallback() {
           @Override
           public void onFailure(Request request, IOException e) {
               
           }

           @Override
           public void onResponse(String response) {

           }
       });

3. post 同步请求

		OkHttpClientManager.Param param = new OkHttpClientManager.Param();
        try {
            Response response = OkHttpClientManager.post("url", param);
            String string = response.body().string();\
        } catch (IOException e) {
            e.printStackTrace();
        }

4. post 异步请求(键值对参数)

		Map<String,String> map = new HashMap<>();
        OkHttpClientManager.postAsyn("url", new OkHttpClientManager.StringCallback() {
            @Override
            public void onFailure(Request request, IOException e) {

            }

            @Override
            public void onResponse(String response) {

            }
        },map,null);

5. post 异步请求（Json 参数）

		 OkHttpClientManager.postJson("url", new OkHttpClientManager.StringCallback() {
            @Override
            public void onFailure(Request request, IOException e) {
                
            }

            @Override
            public void onResponse(String response) {

            }
        },new JSONObject());

6. post 异步请求（返回javabean对象）

		    Map<String,String> map = new HashMap<>();
	       OkHttpClientManager.postObject("url", new OkHttpCallBack<LoginBean>(new OkJsonParser<LoginBean>() {
	       }) {
	           @Override
	           public void onSuccess(int code, LoginBean loginBean) {
	
	           }
	
	           @Override
	           public void onFailure(Throwable e) {
	
	           }
	       },map,"");


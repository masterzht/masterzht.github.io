title: Rertofit的使用
author: Machinezht
date: 2018-04-04 08:18:09
tags:
---
retrofit是一个网络请求库，它是根据okhttp改造的，底层实现还是okhttp，它自身还封装了解析html，json等等的库，用于更便利的restful风格的数据。（python最近也出现了个库requests-html，把请求和解析都封装好了，过一段时间，我会描述一下这个库的简单使用）
目前retrofit的最新版本是2.4.0,我会基于这个版本做简单的使用介绍
<!--more-->

一般情况下两部分即可完成

```
public interface Api {
	 String URL = "http://www.weather.com.cn/";
	//http://www.weather.com.cn/adat/sk/{cityId}.html
	@GET("adat/sk/{cityId}.html")
    Call<ResponseBody> getWeather(@Path("cityId") String cityId);

	//解析为bean数据
	@GET("adat/sk/{cityId}.html")
	Call<Weather> getWeather_Gson(@Path("cityId") String cityId);

}
```

接下来设置网络请求

```
Retrofit retrofit = new Retrofit.Builder()                //这里建议：- Base URL: 总是以/结尾；- @Url: 不要以/开头
                 .baseUrl(Api.URL)
                 //.addConverterFactory(GsonConverterFactory.create())
                 .build();
         Api apiStores = retrofit.create(Api.class);
         Call<ResponseBody> call = apiStores.getWeather("101010100");
         try {
             Response<ResponseBody> bodyResponse = call.execute();
             String body = bodyResponse.body().string();//获取返回体的字符串
             //Log.i("wxl", "body=" + body);
             System.out.println(body);
         } catch (IOException e) {
             e.printStackTrace();
         }
```         

就这样几步就完成了weather服务端请求，还可以添加json的解析只要添加相应的json解析库及bean即可解析。

![upload successful](\assets\online_img\weather.png)

在我的github里面有retrofit使用的具体详细案例：[https://github.com/masterzht/Study-Notes/tree/master/Java/retrofit%E4%BD%BF%E7%94%A8](https://github.com/masterzht/Study-Notes/tree/master/Java/retrofit%E4%BD%BF%E7%94%A8)
    
    
    
    
    
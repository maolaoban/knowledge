max-age: 将要过期的最大秒数，设置为 -1 即可删除
expires: 将要过期的绝对时间，存储到 cookies 中需要通过 date.toUTCString() 处理，设置为过期时间即可删除

eg:
     document.cookie = "a=3; max-age=-1";
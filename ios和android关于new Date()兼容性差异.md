### ios和android关于new Date()兼容性差异

Android ：new Date('2021-01-22 14:25:20').getTime();

ios : new Date('2021/01/22 14:25:20').getTime();



"2021-01-22 14:25:20".replace(/-/g, "/")  ==> '2021/01/22 14:25:20'

ios上不能写24:00:00，new Date('2021/01/22 24:00:00').getTime()  ==> NaN


##  find,filter
```
<!DOCTYPE html>
<html>
<head>
</head>
<body>
    <script>
        var lstVssConfigParaInfo = [{
            "strVssConfigParaName": "FILE_SERVICE_IP",
            "strVssConfigParaValue": "192.168.1.66"
          },
          {
            "strVssConfigParaName": "FILE_SERVICE_PORT",
            "strVssConfigParaValue": "80"
          }]

          var nubip = lstVssConfigParaInfo.find(nub => nub.strVssConfigParaName == "FILE_SERVICE_IP");
          console.log(nubip); //获取的是一条数据

          var nubport = lstVssConfigParaInfo.filter(nub => nub.strVssConfigParaName == "FILE_SERVICE_PORT");
          console.log(nubport); //获取的是一个数组
    </script>
</body>
</html>
```
登录接口使用 ,拿到sessionToken
```
http://prod.dgiotcloud.cn/iotapi/login
```
post方式请求
Content-Type: text/plain
测试登录  账号：13313131319    密码：13313131319
传输格式为：
```
{"password":"13313131319","username":"13313131319"}
```
正确返回内容：
```json
{"ACL":{"Zf94hIumlQ":{"read":true,"write":true}},"createdAt":"2020-11-19T03:22:28.655Z","email":"13313131319@smh.com","emailVerified":true,"nick":"13313131319","objectId":"Zf94hIumlQ","phone":"13313131319","roles":[{"alias":"新马赫","name":"新马赫","org_type":"平台管理员","tag":{"appconfig":{"expires":"21600","file":"http://prod.dgiotcloud.cn:1250/shapes/upload","graphql":"http://prod.dgiotcloud.cn/iotapi/graphql","home":"E:/shuwa/4.1.0/shuwa_data_center/datacenter/file/files","rest":"http://prod.dgiotcloud.cn/iotapi","secret":"VDEzNjI1MjMxNjAzMTc2MDY0NjE0","topo":"http://prod.dgiotcloud.cn:1350/"}}}],"sessionToken":"r:0863d6a55341a13f6bd4436521901d1b","updatedAt":"2020-11-19T03:22:28.750Z","username":"13313131319"}
```

获取服务器分配的公司的objectId,为了后面的请求接口使用
两个请求链接为一个，上面的参数为unicode转码，
```
http://prod.dgiotcloud.cn/iotapi/classes/Product?where=%7B%22nodeType%22:1%7D
http://prod.dgiotcloud.cn/iotapi/classes/Product?where={"nodeType":1}
```
get方式请求 ，请求时带上 sessionToken 传输格式为:sessionToken: 获取到的sessionToken值
正确返回内容:
```json
{"results":[{"objectId":"0765bee775","createdAt":"2020-09-03T01:28:35.265Z","updatedAt":"2021-03-18T04:03:02.227Z","category":"IotHub","config":{"name":"图层","layer":{"width":800,"height":600,"backColor":"#eee","backgroundImage":"","widthHeightRatio":""},"components":[{"name":"text0","type":"text","style":{"text":"Test","zIndex":1,"visible":true,"fontSize":14,"position":{"h":30,"w":100,"x":125,"y":89},"backColor":"rgba(46,176,80,1)","foreColor":"#000000","textAlign":"center","transform":0,"fontFamily":"Arial","borderColor":"#ccccccff","borderStyle":"solid","borderWidth":0},"action":[],"handle":"","dataBind":{"sn":"","biz":"","title":"","queryParam":{}},"iconName":"text_fields","wumoxing":{"max":1,"min":0,"step":0,"unit":"","value":[],"identifier":"AgreementState"},"productId":"0765bee775","identifier":"709e52bf-2d8e-426e-b3d9-cd87b9510ada"}]},"desc":"","devType":"sinmahe_PeriodicInformation","dynamicReg":true,"icon":"","name":"新马赫运行数据","netType":"CELLULAR","nodeType":1,"productSecret":"SDc1MzA4NDMxNTk5MDk2NTE1OTI1","thing":{"properties":[{"name":"关机确认时间","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"normal","quantity":0,"byteorder":"big"},"dataType":{"type":"int","specs":{"max":168,"min":1,"step":0,"unit":""}},"required":true,"accessMode":"r","identifier":"PowerOffDelay"},{"name":"协议状态","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"normal","quantity":0,"byteorder":"big"},"dataType":{"type":"int","specs":{"max":1,"min":0,"step":0,"unit":""}},"required":true,"accessMode":"r","identifier":"AgreementState"},{"name":"电梯运行状态","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"normal","quantity":0,"byteorder":"big"},"dataType":{"type":"int","specs":{"max":3,"min":0,"step":1,"unit":""}},"required":true,"accessMode":"r","identifier":"RunState"},{"name":"目标楼层","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"int","specs":{"max":500,"min":-10,"step":1,"unit":""}},"required":true,"accessMode":"r","identifier":"AimLayer"},{"name":"运行层","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"int","specs":{"max":500,"min":-10,"step":1,"unit":""}},"required":true,"accessMode":"r","identifier":"RunLayer"},{"name":"当前楼层","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"int","specs":{"max":500,"min":-10,"step":1,"unit":""}},"required":true,"accessMode":"r","identifier":"CurrLayer"},{"name":"发布频率控制","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"int","specs":{"max":1000,"min":1,"step":1,"unit":""}},"required":true,"accessMode":"r","identifier":"PubFreq"},{"name":"自重","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"float","specs":{"max":30000,"min":0,"step":0.01,"unit":"kg"}},"required":true,"accessMode":"r","identifier":"DeadLoad"},{"name":"净重","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"float","specs":{"max":30000,"min":0,"step":0.01,"unit":"kg"}},"required":true,"accessMode":"r","identifier":"NetWeight"},{"name":"操作台通信状态","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"int","specs":{"max":1,"min":0,"step":0.5,"unit":""}},"required":true,"accessMode":"r","identifier":"ConsoleComm"},{"name":"HMI 通信状态","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"int","specs":{"max":1,"min":0,"step":0.5,"unit":""}},"required":true,"accessMode":"r","identifier":"HMIComm"},{"name":"运行阶段","dataForm":{"rate":1,"offset":0,"address":"0","protocol":"","quantity":0,"byteOrder":""},"dataType":{"type":"int","specs":{"max":7,"min":0,"step":1,"unit":""}},"required":true,"accessMode":"r","identifier":"Run
```
获取设备列表
get方式请求 ，请求时带上 sessionToken 传输格式为:sessionToken: 获取到的sessionToken值
两个请求链接为一个，上面的参数为unicode转码，
```
http://prod.dgiotcloud.cn/iotapi/classes/Device?skip=0&keys=count%28*%29&limit=20&order=-createdAt&where=%7B%22product%22%3A%220765bee775%22%7D
http://prod.dgiotcloud.cn/iotapi/classes/Device?skip=0&keys=count(*)&limit=20&order=-createdAt&where={"product":"0765bee775"}
```
参数skip和limit为分页使用，where是请求回来的objectid，其他参数为默认的，不需要改动

+ skip：当前页数 从0开始
+ limit：一页请求多少条数据 可以为20
+ where：把0765bee775替换成你获取到的值
正确的返回结果
```
{"count":239,"results":[{"ACL":{"role:徐州万都":{"read":true,"write":true}},"basedata":{"71004722":1609344000,"PowerState":1,"RunState":0,"basicdata":{"CtrSoftVersion":"0.1.1","CtrlSerialNo":"202007023288","FOTA":0,"GPS":{"Lat":34.284877,"Lon":117.231525},"Lat":34.284877,"LearnedLayer":0,"Lon":117.231525,"MDSerialNo":"22222222","MDSoftVersion":"1.0.1","ParaGet":0,"PowerOnCtrl":0,"ProtocolVersion":"1.0.1","PubCtrl":1,"PubFreq":20,"RatedFreq":50,"RatedLoad":2000,"RatedPower":37,"SIMSerialNo":"89860403102070226779","SelfAdjust":0,"SelfLearned":0,"SerialNo":"12345678","SumLayer":1,"WeightFactor":360,"baiduaddr":{"addressComponent":{"adcode":"320302","city":"徐州市","city_level":2,"country":"中国","country_code":0,"country_code_iso":"CHN","country_code_iso2":"CN","direction":"","distance":"","district":"鼓楼区","province":"江苏省","street":"G104(旧)","street_number":"","town":"","town_code":""},"business":"金山桥,下淀","cityCode":316,"formatted_address":"江苏省徐州市鼓楼区G104(旧)","location":{"lat":34.28994903010745,"lng":117.24363160060703},"poiRegions":[],"pois":[],"roads":[],"sematic_description":""},"mapAddressText":"","partAddr":"71004722"},"expirationTime":1609344000,"factory":"新马赫发货"},"createdAt":"2021-02-02T05:59:50.407Z","detail":{"factory":"徐州万都"},"devaddr":"20110768","isEnable":true,"name":"万都202011624","objectId":"MjGFmO6nKB","product":{"__type":"Pointer","className":"Product","objectId":"0765bee775"},"route":{},"status":"ONLINE","updatedAt":"2021-02-02T05:59:50.407Z"}]}
```

获取设备的状态详情接口
```
http://prod.dgiotcloud.cn/iotapi/device
```
post请求方式，请求时带上 sessionToken 传输格式为:sessionToken: 获取到的sessionToken值
请求传输参数：
```
{"order":"-createdAt","where":{"objectId":{"$in":["MjGFmO6nKB"]}}}
```
MjGFmO6nKB参数为：你想查看设备的 objectId。
正确的返回结果；
```json
{"results":[{"ACL":{"role:徐州万都":{"read":true,"write":true}},"basedata":{"71004722":1609344000,"PowerState":1,"RunState":0,"basicdata":{"CtrSoftVersion":"0.1.1","CtrlSerialNo":"202007023288","FOTA":0,"GPS":{"Lat":34.284877,"Lon":117.231525},"Lat":34.284877,"LearnedLayer":0,"Lon":117.231525,"MDSerialNo":"22222222","MDSoftVersion":"1.0.1","ParaGet":0,"PowerOnCtrl":0,"ProtocolVersion":"1.0.1","PubCtrl":1,"PubFreq":20,"RatedFreq":50,"RatedLoad":2000,"RatedPower":37,"SIMSerialNo":"89860403102070226779","SelfAdjust":0,"SelfLearned":0,"SerialNo":"12345678","SumLayer":1,"WeightFactor":360,"baiduaddr":{"addressComponent":{"adcode":"320302","city":"徐州市","city_level":2,"country":"中国","country_code":0,"country_code_iso":"CHN","country_code_iso2":"CN","direction":"","distance":"","district":"鼓楼区","province":"江苏省","street":"G104(旧)","street_number":"","town":"","town_code":""},"business":"金山桥,下淀","cityCode":316,"formatted_address":"江苏省徐州市鼓楼区G104(旧)","location":{"lat":34.28994903010745,"lng":117.24363160060703},"poiRegions":[],"pois":[],"roads":[],"sematic_description":""},"mapAddressText":"","partAddr":"71004722"},"expirationTime":1609344000,"factory":"新马赫发货"},"createdAt":"2021-02-02T05:59:50.407Z","detail":{"factory":"徐州万都"},"devaddr":"20110768","isEnable":true,"lasttime":0,"name":"万都202011624","objectId":"MjGFmO6nKB","route":{},"status":"ONLINE","swtopo":{},"tddata":[{"data":{},"deviceid":"MjGFmO6nKB","productid":"0765bee775"}],"updatedAt":"2021-02-02T05:59:50.407Z"}]}
```
返回结果是demo的事例，具体返回接口的参数可以由自己定义，具体请询问客服。

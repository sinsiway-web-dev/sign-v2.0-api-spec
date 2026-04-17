# JDBC - 연결 테스트
보안 대상 DB 상태 확인에 사용하는 JDBC 연결 테스트 입니다.
## URL
* /api/sign/jdbc/connectionTest
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*dbType|11|int|Petra db type|
|*jdbcUrl|jdbc:oracle:thin:@192.168.10.110:1522:prod|String|JDBC URL|
|*dbAccount|hr|String|DB 계정|
|*dbPassword|hr|String|DB 비밀번호|
|version|5|String|변경 대상 버전|
```
?dbType=11&jdbcUrl=jdbc:oracle:thin:@192.168.10.110:1522:prod&dbAccount=hr&dbPassword=hr&version=5
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "data": {},
    "message": ""
}
```

# JDBC - 드라이버 확인
요청받은 DB 버전에 맞는 드라이버가 있는지 확인합니다.
## URL
* /api/sign/jdbc/driver
* GET
* application/x-www-form-urlencoded;charset=UTF-8
## Request
|항목|값(예시)|타입|설명|
|---|---|---|---|
|*dbType|11|int|Petra db type|
|*version|5|String|변경 대상 버전|
```
?dbType=11&version=5
```
## Response
|항목|값(예시)|타입|설명|
|---|---|---|---|
|code|200|int|결과 코드|
|data||Map|결과 데이터|
|isSupported|true|boolean|결과 데이터|
|message||String|결과 메시지|
```json
{
    "code": 200,
    "message": "처리되었습니다.",
    "data": {
        "isSupported": true
    }
}
```

```json
{
    "code": 200,
    "message": "[oracle] 요청된 버전(21)에 해당하는 JDBC 드라이버를 찾을 수 없습니다. jdbcdrivers.json 설정을 확인하세요.",
    "data": {
        "isSupported": false
    }
}
```

## 清元链 NFT

### 创建链账户

接口: QyNftCreateAccountAddressService

描述: 创建用户链账户； 

**输入参数**

名称 | 类型 | 必须 | 说明 
---|:---:|:---:|---
appid | str | Y | appid 
secret | str | Y | 秘钥 
name | str | Y | 用户姓名 
idc | str | Y | 用户身份证号 
mobile | str | Y | 用户手机号 

**输出参数**

 名称 | 类型 | 说明 
---|:---:|---
 code | int | 返回码 
 msg | str | 返回说明 
 data |  |
 -- address | str | 链账户地址 

**返回示例**

```
{
	"code": 200, 
	"msg": "success", 
	"data": {
		"address": "0xa84e3179e752dfcd1577a24489cb805a395b35d2"
	}
}
```

**接口示例**

```
   @Test
    void testCreateAccount() {
	QyNftCreateAccountAddressService qyNftCreateAccountAddressService = new QyNftCreateAccountAddressService();
        String account = qyNftCreateAccountAddressService.createAccount(appid, secret, name, idc, mobile);
        logger.info(account);
    }

>> {"code": 200, "msg": "success", "data": {"address": "0xa84e3179e752dfcd1577a24489cb805a395b35d2"}}
```



### 创建NFT资源

接口: QyNftCreateNftService

描述: 创建NFT资源； 

**输入参数(对象Nft传参)**


名称       | 类型  | 必须 | 说明            
---|:---:|:---:|---
| appid       | str  |  Y   | appid           |
| secret      | str  |  Y   | 秘钥             |
| title       | str  |  Y   | NFT资源名称      |
| address     | str  |  Y   | NFT拥有者链账户   |
| author      | str  |  Y   | 作者            |
| url         | str  |  Y   | NFT资源地址     |
| series_id   | str  |  N   | 系列ID          |
| series_name | str  |  N   | 系列名称        |
| note        | str  |  N   | 备注说明        |

**输出参数**

 名称             | 类型 | 说明
---|:---:|---
| code             | int  | 返回码      |
| msg              | str  | 返回说明    |
| data             |      |             |
| -- Payload       | str  |             |
| -- TokenId       | str  | TOKEN ID    |
| -- SourceUrl     | str  | NFT资源地址 |
| -- TransactionID | str  | 交易ID      |

**返回示例**
```
{
	"code": 200, 
	"msg": "success", 
	"data": {
		"Payload": "", 
		"TokenId": "84820430ce15ebe13789596f544df1123226197baca3e6f8fdded2e422f2aec7", 
		"TransactionID": "84820430ce15ebe13789596f544df1123226197baca3e6f8fdded2e422f2aec7", 
		"SourceUrl": "http://openqkl.newmin.cn/resouce/bOQCjI57wbka4ZqAGDBFkOuv2NrMR9"
	}
}
```

**接口示例**
[注]:下方示例仅给出必填字段，如您需要非必填字段，需要传值，则set添加值
```
    @Test
    void testCreateNft() {
	QyNftCreateNftService qyNftCreateNftService = new QyNftCreateNftService();
        Nft nft = new Nft();
        nft.setAppid(api);
        nft.setSecret(secret);
        nft.setTitle(title);
        nft.setAddress(address);
        nft.setAuthor(author);
        nft.setUrl(url);
        String createNft = qyNftCreateNftService.createNft(nft);
        logger.info(createNft);
    }

>> {"code": 200, "msg": "success", "data": {"Payload": "", "TokenId": "84820430ce15ebe13789596f544df1123226197baca3e6f8fdded2e422f2aec7", "TransactionID": "84820430ce15ebe13789596f544df1123226197baca3e6f8fdded2e422f2aec7", "ResouceUrl": "http://openqkl.newmin.cn/resouce/bOQCjI57wbka4ZqAGDBFkOuv2NrMR9"}}
```



### 铸造NFT

接口: QyNftCastingNftService

描述: 将NFT资源上链进行铸造NFT； 

**输入参数**

| 名称        | 类型 | 必须 | 说明                                 |
---|:---:|:---:|---
| appid       | str  |  Y   | appid                                |
| secret      | str  |  Y   | 秘钥                                 |
| source_url  | str  |  Y   | NFT资源地址  通过创建NFT资源接口获取 |
| order_sn    | str  |  Y   | 订单号                               |

**输出参数**

| 名称             | 类型 | 说明     |
---|:---:|---
| code             | int  | 返回码   |
| msg              | str  | 返回说明 |
| data             |      |          |
| -- Hash          | str  | 交易哈希 |
| -- TransactionID | str  | 交易ID   |


**返回示例**

```
{
	"code": 200, 
	"msg": "success", 
	"data": {
		"Payload": "", 
		"TransactionID": "1c4078661f14590fe929db4f509163028adc26fe5b30b97900a4f8f7e1314330", 
		"Hash":"5fb9ea47def28d29bc4f6ed78b53264cb46938b8f1b77cb445a3c91009521739"
	}
}
```

**接口示例**

```
   @Test
    void testCreationNft() {
	QyNftCastingNftService qyNftCastingNftService = new QyNftCastingNftService();
        String creationNft = qyNftCastingNftService.castingNft(appid, secret, source_url, order_sn);
        logger.info(creationNft);
    }

>> {"code": 200, "msg": "success", "data": {"Payload": "", "Hash":"5fb9ea47def28d29bc4f6ed78b53264cb46938b8f1b77cb445a3c91009521739", "TransactionID": "1c4078661f14590fe929db4f509163028adc26fe5b30b97900a4f8f7e1314330"}}


```



### NFT转移

接口: QyNftTransFromService

描述: 将NFT资源上链进行铸造NFT； 

**输入参数**

| 名称         | 类型 | 必须 | 说明                |
---|:---:|:---:|---
| appid        | str  |  Y   | appid               |
| secret       | str  |  Y   | 秘钥                |
| address_from | str  |  Y   | NFT归属者链账户地址 |
| address_to   | str  |  Y   | NFT接收方链账户地址 |
| token_id     | str  |  Y   | Token ID            |

**输出参数**

| 名称             | 类型 | 说明     |
---|:---:|---
| code             | int  | 返回码   |
| msg              | str  | 返回说明 |
| data             |      |          |
| -- TransactionID | str  | 交易ID   |
| -- Payload       | str  |          |

**返回示例**

```
{
	"code": 200, 
	"msg": "success", 
	"data": {
		"Payload": "", 
		"TransactionID": "bd5ca48ee2488d0837dae8be7ed6148d73399177effd485e63f9803a2e2648b5"
	}
}
```

**接口示例**

```
  @Test
    void transFrom() {
	  QyNftTransFromService qyNftTransFromService = new QyNftTransFromService();
        String transFrom = qyNftTransFromService.transFrom(appid, secret, address_from, address_to, token_id);
        logger.info(transFrom);
    }

>> {"code": 200, "msg": "success", "data": {"Payload": "", "TransactionID": "bd5ca48ee2488d0837dae8be7ed6148d73399177effd485e63f9803a2e2648b5"}}
```



### NFT销毁

接口: QyNftDestructionService

描述: 将链上NFT销毁； 

**输入参数**

| 名称         | 类型 | 必须 | 说明                |
---|:---:|:---:|---
| appid        | str  |  Y   | appid               |
| secret       | str  |  Y   | 秘钥                |
| address_from | str  |  Y   | NFT归属者链账户地址 |
| token_id     | str  |  Y   | Token ID            |

**输出参数**

| 名称             | 类型 | 说明     |
---|:---:|---
| code             | int  | 返回码   |
| msg              | str  | 返回说明 |
| data             |      |          |
| -- TransactionID | str  | 交易ID   |
| -- Payload       | str  |          |

**返回示例**

```
{
	"code": 200, 
	"msg": "success", 
	"data": {
		"Payload": "", 
		"TransactionID": "5a1b9036a37253fc831f68cfbb482f75dd273427d898689e567a3ca1127bc8d4"
	}
}
```

**接口示例**

```
  @Test
    void destruction() {
	QyNftDestructionService qyNftDestructionService = new QyNftDestructionService();
        String destruction = qyNftDestructionService.destruction(appid, secret, address_from, token_id);
        logger.info(destruction);
    }

>> {"code": 200, "msg": "success", "data": {"Payload": "", "TransactionID": "5a1b9036a37253fc831f68cfbb482f75dd273427d898689e567a3ca1127bc8d4"}}
```



### 查询某账户拥有的NFT

接口: QyNftGetBalanceofService

描述: 查询某账户下拥有的NFT信息； 

**输入参数**

| 名称    | 类型 | 必须 | 说明       |
---|:---:|:---:|---
| appid   | str  |  Y   | appid      |
| secret  | str  |  Y   | 秘钥       |
| address | str  |  Y   | 链账户地址 |

**输出参数**

| 名称     | 类型  | 说明                               |
---|:---:|---
| code     |  int  | 返回码                             |
| msg      |  str  | 返回说明                           |
| data     |       |                                    |
| -- Count |  int  | 拥有NFT总数                        |
| -- List  | array | 拥有NFT列表｛TOKENID:NFT资源地址｝ |

**返回示例**

```
{
	"code": 200, 
	"msg": "success",  
	"data": {
		"Count": 1, 
		"List": {'11a4f81dc2eb44dda24f94f2492c62729b5a2a02f5eebb4e21a150e282ded21e": "http://openqkl.newmin.cn/resouce/1Ivid5vTCkGwG0RbwYbLITOFQrZXl4?tokenId=11a4f81dc2eb44dda24f94f2492c62729b5a2a02f5eebb4e21a150e282ded21e"
		}, 
		"TransactionID": "09e52b2bd84d121d57964a205a0c1a22d8ac64ebeba6ffd805ff03cd75e8f01a"
	}
}
```

**接口示例**

```
@Test
    void getBalanceof() {
	QyNftGetBalanceofService qyNftGetBalanceofService = new QyNftGetBalanceofService();
        String getBalanceof = qyNftGetBalanceofService.getBalanceof(appid, secret, address);
        logger.info(getBalanceof);
    }
>> {"code": 200, "msg": "success", "data": {"Count": 1, "List": {"11a4f81dc2eb44dda24f94f2492c62729b5a2a02f5eebb4e21a150e282ded21e": "http://openqkl.newmin.cn/resouce/1Ivid5vTCkGwG0RbwYbLITOFQrZXl4?tokenId=11a4f81dc2eb44dda24f94f2492c62729b5a2a02f5eebb4e21a150e282ded21e"}, "TransactionID": "09e52b2bd84d121d57964a205a0c1a22d8ac64ebeba6ffd805ff03cd75e8f01a"}}

```



### 查询NFT上链存证信息

接口: QyNftQueryService

描述: 查询交易哈希获取上链的存证信息； 

**输入参数**

| 名称   | 类型 | 必须 | 说明     |
---|:---:|:---:|---
| appid  | str  |  Y   | appid    |
| secret | str  |  Y   | 秘钥     |
| hash   | str  |  Y   | 交易哈希 |

**输出参数**

| 名称             | 类型 | 说明        |
---|:---:|---
| code             | int  | 返回码      |
| msg              | str  | 返回说明    |
| data             |      |             |
| -- Info          | dict | NFT存证信息 |
| -- TransactionID | str  | 交易ID      |

**返回示例**
```
{
  "code": 200,
  "msg": "success",
  "data": {
    "Info": {
      "author": "张三",
      "title": "孙悟空卡片",
      "series_name": null,
      "series_id": null,
      "url": "http://www.qingyuan.com/logon.jpg"
    },
    "TransactionID": "3c1c332ed9dc7d537971bac460026133c8b40992dda5496cc299e18c0d252020"
  }
}

```

**接口示例**

```
   @Test
    void nftQuery() {
    QyNftQueryService qyNftQueryService = new QyNftQueryService();
        String nftQuery = qyNftQueryService.nftQuery(appid, secret, hash);
        logger.info(nftQuery);
		}

>> {"code":200,"msg":"success","data":{"Info":{"author":"张三","title":"孙悟空卡片","series_name":null,"series_id":null,"url":"http://www.qingyuan.com/logon.jpg"},"TransactionID":"3c1c332ed9dc7d537971bac460026133c8b40992dda5496cc299e18c0d252020"}}
```


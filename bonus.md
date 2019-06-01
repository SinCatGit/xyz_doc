
## 通过G串查看源铸平台场外分红

**Request**

    GET api/jet_bonuses/:token_g?{curr, limit, status}

**Arguments**

字段 | 字段类型 | 描述 | 例子
--- | --- | --- | ---
token_g | required, string | 用户G串 | GBPZCIXXXI52U76
cursor | required, string | 当前页数 | 0
limit | required, string | 最大条数 | 10
status | string | 分红状态 (0:未领取，1:处理中，2:已领取) 查全部为空 | 0


**Response**

字段 | 字段类型 | 描述 | 例子
--- | --- | --- | ---
msg | required，string | 信息 | ok
status | required，integer | 执行结果(成功：0，失败：-1) | 
data | string | 分红记录列表数据 | 见下文
total | required, int | 总数 | 500
cursor | required, string | 当前页数 | 0
limit | required, int | 最大条数 | 10

*data*

字段 | 字段类型 | 描述 | 例子
--- | --- | --- | ---
min_bonus_id | required，string | ID | ok
asset_code | required，string | 资产代码 | XLM
bonus_amount | required，string | 数量 | 10 * 10^8
bonus_time | required，datetime | 分红时间 | 2019年6月1日12点14分23秒
bonus_receive_time | required，datetime | 领取时间 | 2019年6月1日12点14分23秒
status | required，string | 分红状态 | 0：未领取，1：处理中，2：已领取
tx_id | string | 已领取分红ID | 455d8b8435eac9ed1b638466deda6


**Example**

*request:*
```
curl https://yuanzhu.io/api/jet_bonuses/GBPZCIY3QWHT5ZVC5DBEITYSU5N45ULPYETUE46Z2MQUK3WK75I52U76?curr=1&limit=10
```
*respone:*
```
{
  "msg": "OK",
  "status": 0,
  "data": [
    {
      "min_bonus_id": "a35706e60e584af7a6bf52ed94eed61c",
      "asset_code": "XLM",
      "bonus_amount": 286428,
      "bonus_time": "2019-05-30 00:15:00.000",
      "bonus_receive_time": "2019-05-30 00:00:00.921",
      "status": 0,
      "tx_id": null
    }
  ],
  "total": 1,
  "curr": 1,
  "limit": 10
}
```
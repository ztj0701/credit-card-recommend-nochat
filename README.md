【基本信息】
接口地址：https://你的域名/recommend
请求方式：POST
Content-Type：application/json


【请求内容示例】
{
  "年收入": "20-50万",
  "年消费额": "20000以上",
  "权益": "现金返现"
}



【正确返回结果示例（最多返回三张卡）】
[
  {
    "id": 1,
    "name": "招商银行VISA全币种白金信用卡",
    "benefits": [
      "龙腾境外机场贵宾厅无限次",
      "境外消费最高返现2%",
      "全币种免换汇"
    ]
  },
  {
    "id": 2,
    "name": "...",
    "benefits": [
      "...",
      "...",
      "..."
    ]
  }
]


【错误示例】
{
  "error": "缺少必要参数"
}


【在小程序中代码调用示例】
wx.request({
  url: 'https://你的域名/recommend',
  method: 'POST',
  data: {
    "年收入": "20-50万",
    "年消费额": "20000以上",
    "权益": "现金返现"
  },
  header: {
    'content-type': 'application/json'
  },
  success(res) {
    if (res.statusCode === 200) {
      // 处理推荐结果
      const recommendations = res.data;
      console.log('推荐的信用卡:', recommendations);
    } else {
      // 处理错误
      console.error('请求失败:', res.data.error);
    }
  },
  fail(err) {
    console.error('请求错误:', err);
  }
});

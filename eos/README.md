# mds-eosjs

## A EOS jQuery plugin for Math Wallet APP

麦子钱包 EOS DAPP 插件（基于 jQuery）

### File Specification

+ jquery.mdseos.js -- For EOS


### Tutorial

This plugin is used for interaction between DAPP (Web) and the Math Wallet APP.

Simple way to use it:


##### 1. Please initialize BP information before using the plugin:

``` javascript
$.mdseos.init(
  {"nodes":[
    {"jsonRpc":"https:\/\/eostestnet.medishares.net",'chainID' => '2fd52147e10512439ec675898682d1baff40a5d530726244600ba145e2393444'}, // 0: testnet-node
    {"jsonRpc":"https:\/\/eosmainnet.medishares.net",'chainID' => '2fd52147e10512439ec675898682d1baff40a5d530726244600ba145e2393444'}  // 1: mainnet-node
  ]}
);
```

Note: for eosforce mainnet, please use jsonRpc https://w1.eosforce.cn or https://w2.eosforce.cn

##### 2. Get the account of current wallet:

``` javascript
$.mdseos.app_get_account(
  function(account_info){
    console.log(account_info) //app return like this -- {"account":"medisharesbp","node":"1"}
    console.log($.mdseos.getAccount()) //getAccount() will return the latest account from app or setAccount()
  } //callback
)
```


##### 3. Query informaiton，for example: get_currency_balance:

``` javascript
$.mdseos.get_currency_balance(
  function(balance){
    console.log(balance)
  },//callback
  "medisharesbp", //account
  function(){
    alert('failed!')
  }
);
```


##### 4. Create action (for example: purchase RAM):

``` javascript
$.mdseos.create_action_buyram(
  function(action){
    console.log(action)
  },
  $.mdseos.getAccount(), // buyram payer
  $.mdseos.getAccount(), // buyram receiver
  '1.0000 EOS', // buyram quant
  false, // to Bin ( app sign set false)
  failedCallback // failed callback
);
```


##### 5. Sign transaction:

``` javascript
$.eosforce.app_sign_transaction(
  function(transData){
    console.log(transData) //signed transaction
  }, //signed callback
  transaction, //transaction
  function(){
    alert('failed!')
  }  //failed callback
);
```

Note: this function will call APP's current EOS account and return the signed transaction data.


##### 6. Push tansaction:

``` javascript
$.mdseos.push_transaction_all(
  function(){
    alert('Success');
  }, //callback
  transData, //signed transaction from app
  function(){
    alert('failed!')
  } //failed callback
);
```


### Testing

Math Wallet also provide a testing tool in [DApp] - [EOS DAPP Developer Browser] where you can enter your DAPP URL and test the functions.

![](https://github.com/MediShares/mds-eosjs/blob/master/image/testing.jpg)


### ETH DAPP Developer

For ETH developer, we use the same web3 API as metamask.

https://github.com/MetaMask/faq/blob/master/DEVELOPERS.md


### Download Math Wallet 麦子钱包下载

[http://mathwallet.org](http://mathwallet.org)

If you would like to list your DAPP in Math Wallet, please send your DAPP information to hello@medishares.org

如果您希望将您开发的DAPP加入麦子钱包，请通过邮箱联系我们 hello@medishares.org
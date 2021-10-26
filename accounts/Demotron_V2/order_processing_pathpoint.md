# Order Processing 

The Demotron V2 account contains a fairly detailed microservice tier dedicated to a fictional Order Processing flow.

## Stages

### Order Management

#### APM Sources
 - [Order-Processing](https://onenr.io/0PLRE0Xqowa)
 - [Order-Composer](https://onenr.io/06vjAJDYDQP)
 - [Order-Status](https://onenr.io/0WBQ1JxE9wx)
 - [Billing-Service](https://onenr.io/0GbRmlyMVwy)
 - [Inventory](https://onenr.io/0kERzGmrAjr)

#### Infra Sources (Examples)

- Order Composer Pod Wait: `FROM K8sContainerSample select uniqueCount(podName) where status = 'Waiting' and podName like 'order-composer-%'`

#### Packaging

#### APM Sources

- [Order-Packaging](https://onenr.io/0xVwgm8EEjJ)
- [Order-Assembly](https://onenr.io/0eqwyG35Xjn)
- [Box](https://onenr.io/0znQxGeo5jV)
- [Bubble-Wrap](https://onenr.io/0LkjnDbx6wo)
- [Packing-Room](https://onenr.io/0a2wdPBlMwE)
- [Inventory](https://onenr.io/0Zyw4z74Mj3)
- [Inventory-Service](https://onenr.io/0GbRmlyaWwy)

#### Browser Sources
- Home Page: `FROM BrowserInteraction select percentile(duration, 95) where appName = 'WebPortal' where browserInteractionName = 'webportal.telco.nrdemo.com:80/index.html'`
- Browse Product: `FROM BrowserInteraction select percentile(duration, 95) where appName = 'WebPortal' where browserInteractionName = 'webportal.telco.nrdemo.com:80/browse/phones/*'`
- Cart Activity: `FROM BrowserInteraction select percentile(duration, 95) where appName = 'WebPortal' where browserInteractionName = 'webportal.telco.nrdemo.com:80/shoppingcart'`

#### Database Sources
- `SELECT average(provider.readLatency.Average) from DatastoreSample where displayName = 'planservicedbtelcoprod'`

#### Infra Sources (Examples)

- Inventory Pod Wait: `FROM K8sContainerSample select uniqueCount(podName) where status = 'Waiting' and podName like  'inventory%'`

### Shipping

#### APM Sources

- [Shipping-Service](https://onenr.io/0kLwG085KR6)
- [Shipment-Label](https://onenr.io/0xVwgm8mBjJ)
- [Delivery](https://onenr.io/0gbRK0Ge9jE)

#### Infra Sources (Examples)

- Shipping Pod Wait: `FROM K8sContainerSample select uniqueCount(podName) where status = 'Waiting' and podName like  'shipping%'`

###  Notification

#### APM Sources

- [Email-Notification](https://onenr.io/0Zyw4z7zVj3)
- [SMS-Notification](https://onenr.io/0X8wo4YDYRx)

#### Infra Sources (Examples)

- Notification Pod Wait: `FROM K8sContainerSample select uniqueCount(podName) where status = 'Waiting' and podName like  '%-notification-%'`



![OrderComposerServiceMap.png](OrderComposerServiceMap.png)


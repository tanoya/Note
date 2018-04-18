#Order API
##### `public List<OrderDetail> getOrderDetails()`
*注*
获取订单详情
```
public static String getUserOrders(long iCorpId, long iMemeberId,
									Integer pageSize, Integer pageIndex, String status,
									String payStatus, String searchOrderNo, String productNo,
									String startDate, String endDate)
```
*注*
获取用户订单，包括删除的订单数据(`iDelete=1`)
```
public static String getAllOrdersForNextStatus(long iCorpId, long iMemeberId,
			String statuscode, String payStatus, Integer pageSize,
			Integer pageIndex, String searchOrderNo, String productNo,
			String startDate, String endDate,String searchBuyer,
			String searchReceiver,String searchTel,String product,String tagname, String payType, String dlyType,
			String groupOrderStatus, String groupActivityName, Long groupActivityId)
```
*注*
订单列表用来根据条件筛选订单数据， 包括删除的订单数据 (`iDelete=1`)
```
public static String findAll(String query, Object params[],
			Integer pageSize, Integer pageIndex, boolean bShowDetail)
```
*注*
根据query条件,分页获取所有订单, 包括删除的订单数据(`iDelete=1`)
```
public static Order getAgentOrderByOrderNo(String cOrderNo, long iAgentId,
											long corpid)
```
*注*
根据参数条件获取订单数据, 包括删除的订单数据(`iDelete=1`)
```
getCountForNextStatusBySubmiter(String cStatusCode,
			long iSubmitId, long corpid)
```
*注*
根据订单的下一个状态值获取订单数数量,
```
getOrderCountForPayment(long iSubmitId, long corpid)
```
*注*
根据获取订单的付款数量,包括删除的订单数据(`iDelete=1`)
```
getAgentOrderByOrderNo(String cOrderNo, long iAgentId,
			long corpid)
```
*注*
根据订单号，会员id，公司id来获取订单，包括删除的订单数据(`iDelete=1`)
```
getMembersOrderByOrderNo(String cOrderNo, long MembersId, long corpid)
```
*注*
根据订单号，会员id，公司id获取订单数据，包括删除的订单数据(`iDelete=1`)
```
getAgentOrderById(long iorderid, long agentid,
			long corpid)
```
*注*
同上
```
isFinishPayment(long iorderid)
```
*注*
同上
```
getAllOrderByOrderNo(String cOrderNo, long corpid)
```
*注*
同上
```
getOrderByOrderNo(String cOrderNo, long corpid)
```
*注*
同上

getOrderByOrderId
getAgentOrders
delOrder
getSummaryOrders
getSummaryOrdersByDate //使用的是原生sql
getSummaryOrdersByDateNew//使用的原生sql
getApiOrders
getApiOrderMap
getApiOrderCount
getOrders
getOrders
getDetailByMember
getUnRemarkDetailByMember
getUnRemarkOrderList
getDetailByCorp
getOrderStatusRecordByOrderNo -->getOrderByOrderNo
getCountByNextStatus
getCountByStatus
getOrderCounts-->getCountByStatus
getOrdersTOP
getProductTOP --> idelete=0
getOrderPriceByMonth 
setOrderAddress -->getOrderByOrderNo
setPrice -->getOrderByOrderNo
setPostage -->getOrderByOrderNo
deliveryOrderByNo -->getOrderByOrderNo
deliveryOrder -->getOrderByOrderNo
getCountByNextStatus
getCountByStatus
getOrderCounts -->getCountByStatus
				-->getCountByNextStatus
closeOrder-->getOrderByOrderNo
confirmTake-->
orderMemo -->getOrderByOrderNo
getOrderByPayNo
getLogisticInfoByOrder-->getLogisticInfo
changeToPAYMONEY -->getOrderByOrderNo
					-->setOrderStatus
changeToDelivery -->setOrderStatus
getSaledProductTop
getSaledMainProductTop
getOrderedProductNum
getReturnMoney-->getOrderByOrderNo
getMemberSelfOrders
sendSaleReturnOrder2EL
sendOrderDetails2EL
sendDistributionOrder2EL
sendDistributionReturn2EL
getCommonOrderStatus
getGroupOrderStatus
setGroupBuyingBatchOrderStatus
canDeleteGroupBuyingActivity
getSingleMemberBuiedCount
getOrdersByStore
batchLeaveWord-->getOrderByOrderNo
getProductSalesByPromotionId
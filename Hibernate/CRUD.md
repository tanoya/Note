#hibernate 获取数据规则
####*注意*
`hibernate` 在获取数据的时候，先在`缓存`中获取数据，如果`缓存`中找不到与之匹配的数据，然后再向数据库发送请求，获取新的数据。这样处理数据会出现一个问题，数据污染。

*例如*
``` 
public class Product{
	public Long id;
	public String name;
	public double fSalePrice;
	public Integer iQuantity;
	public boolean iStatus; // 上下架状态

	@Transient
	public List<ProductSku> skus;
}

public class ProductSku{
	public Long id;
	public String name;
	public double fSalePrice;
	public Integer iQuantity;
	public boolean iStatus; 
	public Long iProductId; // 属于哪个商品
}

// function 01
public void getPartSkuOfProduct(){
	Product p = Product.findById(1L);
	p.skus = getHalfSkus(); // 此时只获取该商品一般的sku数据
	innerHandler(1L);
	// p.skus 数据添加的是所有的数据
}

// function 02
public void innerHandler(Long iProductId){
	Product p = Product.findById(iProductId);
	p.skus = getAllSkus();
}
```
# ContosoCrafts

***View List Product***
- Create project ASP.NET MVC Core
- Add data folder `wwwroot` ==> `product.json`
- Add Models folder ==> `Product.cs`
- Add Services folder ==> `JsonFileProductService.cs`
- Edit `Startup.cs` ==> `ConfigureServices`
```
    services.AddTransient<JsonFileProductService>();
``` 
- Edit `Index.cshtml.cs`
```
    public IndexModel (ILogger<IndexModel> logger, JsonFileProductService productService)
    { 
        ProductService = productService;
        _logger = logger;
    }

    public JsonFileProductService ProductService { get; } 
    public IEnumerable<Product> Products { get; private set; }

    public void OnGet() 
    {
        Products = ProductService.GetProducts();
    }
```
- Edit Index.cshtml 
```
    @foreach (var product in Model.Products) 
    {
        <h2>@product.Title</h2>
    }
```
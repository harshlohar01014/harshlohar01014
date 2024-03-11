// Product entity class
@Entity(name="product")
public class product {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private string desc;
     double price;
     int category_id;
     int invantary_id;
     int discount_id;
     long create_at;
     long modified_at;
     long deleted_at;
  
   
    private ProductCategory category;
    // getters and setters
}

// ProductCategory entity class
@Entity(name=category")
public class category {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String name;
    private String desc;
    // getters and setters
}

// ProductDiscount entity class
@Entity("discount")
public class discount {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private double discount_Percent;
    private string desc;
    private boolean active;
    long create_at;
     long modified_at;
     long deleted_at;
    
    // getters and setters
}

// ProductInventory entity class
@Entity(name="product_inventory")
public class productinventory {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private int quantity;
    long create_at;
     long modified_at;
     long deleted_at;
    // getters and setters
}

// Product Repository interface
public interface ProductRepository extends JpaRepository<Product, Long> {
    List<Product> findByCategory(ProductCategory category);
}

// Product Service interface
public interface ProductService {
    List<Product> getAllProducts();
    List<Product> getProductsByCategory(ProductCategory category);
    Product getProductById(Long id);
    void addProduct(Product product);
    void updateProduct(Product product);
    void deleteProduct(Long id);
}

// Product Service implementation
@Service
public class ProductServiceImpl implements ProductService {
    @Autowired
    private ProductRepository productRepository;
    
    @Override
    public List<Product> getAllProducts() {
        return productRepository.findAll();
    }
    
    @Override
    public List<Product> getProductsByCategory(ProductCategory category) {
        return productRepository.findByCategory(category);
    }
    
    @Override
    public Product getProductById(Long id) {
        return productRepository.findById(id).orElse(null);
    }
    
    @Override
    public void addProduct(Product product) {
        productRepository.save(product);
    }
    
    @Override
    public void updateProduct(Product product) {
        productRepository.save(product);
    }
    
    @Override
    public void deleteProduct(Long id) {
        productRepository.deleteById(id);
    }
}











public class FactoryMethod {
    public static void main(String[] args) {
        Factory factoryA = new FactoryA();
        // 父类 对象名 = new 子类();

        Product productA = factoryA.createProduct();
        // Product productA = new ProductA();
        productA.info();

        Factory factoryB = new FactoryB();

        Product productB = factoryB.createProduct();
        productB.info();
    }
}

// class Factory
interface Factory {
    public Product createProduct();
}

class FactoryA implements Factory {

    @Override
    public Product createProduct() {
        return new ProductA();
    }
}

class FactoryB implements Factory {

    @Override
    public Product createProduct() {
        return new ProductB();
    }
}

// abstract class Product
interface Product {
    // public abstract void info();
    public void info();
}

// class ProductA extends Product
class ProductA implements Product {

    @Override
    public void info() {
        System.out.println("产品的信息：A");
    }
}

// class ProductB extends Product
class ProductB implements Product {

    @Override
    public void info() {
        System.out.println("产品的信息：B");
    }
}
public class SingletonPattern {
    public static void main(String[] args) {
        // Singleton singleton1 = new Singleton();

        Singleton singleton1 = Singleton.getInstance();
        Singleton singleton2 = Singleton.getInstance();
        Singleton singleton3 = Singleton.getInstance();

        System.out.println(singleton1.getNumber() + " " + singleton2.getNumber() + " " + singleton3.getNumber());

        singleton1.setNumber(528);
        System.out.println(singleton1.getNumber() + " " + singleton2.getNumber() + " " + singleton3.getNumber());

    }
}

class Singleton {
    private int number = 2022;

    public void setNumber(int number) {
        this.number = number;
    }

    public int getNumber() {
        return number;
    }

    private static Singleton instance = new Singleton();

    private Singleton() {
    }

    public static Singleton getInstance() {
        return instance;
    }
}
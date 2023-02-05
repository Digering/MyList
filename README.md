package MyListPapka;

public class Main {
    public static void main(String[] args) {

        MyList list = new MyList();

        list.add(2);
        list.add(5);
        list.add(19);
        list.add(5);

        list.print();

        list.remove(19);

        list.print();
    }
}

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


package MyListPapka;

public class MyList {

    public New head;

    public MyList(){
        head = null;
    }

    public class New{
        public int data;
        public New next;

        public New(int data){
            this.data = data;
            next = null;
        }
    }

    public void add(int data){
        New Newdata = new New(data);
        New Newposition = head;

        if(head == null){
            head = Newdata;
        }else{
            while (Newposition.next != null){
                Newposition = Newposition.next;
            }
            Newposition.next = Newdata;
        }
    }

    public void remove(int data){
        New Newposition = head;
        New TimeNew = null;

        while(Newposition.next != null){
            if (Newposition.data == data){
                if(head == Newposition){
                    head = Newposition.next;
                }else{
                    TimeNew.next = Newposition.next;
                }
                break;
            }
            TimeNew = Newposition;
            Newposition = Newposition.next;
        }

    }

    public void print(){
        New Newposition = head;

        if(head != null){
            System.out.println(head.data);
        }

        while (Newposition.next != null){
            Newposition = Newposition.next;
            System.out.println(Newposition.data);
        }
    }
}

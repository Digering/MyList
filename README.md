package MyListPapka;

public class Main {
    public static void main(String[] args) 

        MyList list = new MyList();

        list.add(2);
        list.add(5);
        list.add(19);
        list.add(5);

        list.print();

        list.remove(19);

        list.print();
    }



package MyListPapka;

public class MyList 

    public New head; // голова списка

    public MyList(){ // конструктор MyList
        head = null; // делаем голову списка изночально пустой
    }

    public class New{
        public int data;
        public New next; // ссылка на следующий элемент

        public New(int data){ // конструктор Node
            this.data = data;
            next = null;
        }
    }

    public void add(int data){ // добавляем элемент
        New Newdata = new New(data);
        New Newposition = head;

        if(head == null){ // если голова пустая
            head = Newdata; // вставляем в нее элемент
        }else{
            while (Newposition.next != null){ // если currentNode имеет ссылку на след. элемент
                Newposition = Newposition.next; // currentNode переходит к след. элементу
            }
            Newposition.next = Newdata; // next ссылается на элемент data
        }
    }

    public void remove(int data){ // удаляем элемент data
        New Newposition = head;
        New TimeNew = null;

        while(Newposition.next != null){ // если currentNode имеет ссылку на след. элемент
            if (Newposition.data == data){ // если currentNode имеет элемент равный data
                if(head == Newposition){ // если элемент data находится в голове
                    head = Newposition.next; // то головой становится след. элемент
                }else{
                    TimeNew.next = Newposition.next;
                }
                break; // прекращать проверку после удаления элемента
            }
            TimeNew = Newposition;
            Newposition = Newposition.next;
        }

    }

    public void print(){ // выводить элементы на экран
        New Newposition = head;

        if(head != null){
            System.out.println(head.data);
        }

        while (Newposition.next != null){
            Newposition = Newposition.next;
            System.out.println(Newposition.data);
        }
    }


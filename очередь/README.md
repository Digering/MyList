<b>в данной программе было реализовано подобие очереди</b>

public class Main 
    public static void main(String[] args) {
        MyQueue queue = new MyQueue();
        queue.Enqueue(2);
        queue.Enqueue(9);
        queue.Enqueue(12);
        queue.Enqueue(6);

        queue.Print();

        System.out.println("");
        System.out.println(queue.Dequeue());
        System.out.println("");

        queue.Print();
        System.out.println("");

        System.out.println(queue.Count());
    }


public class MyQueue 

    private int[] mas;

    public MyQueue(){
    }

    public void Enqueue(int x){
        if(mas == null)
            mas = new int[]{x};
        else{
            int[] mas2 = new int[mas.length+1];
            for(int i=0;i<mas.length;i++){
                mas2[i] = mas[i];
            }
            mas2[mas.length] = x;
            mas = mas2;
        }
    }
    public int Dequeue(){

        if(mas.length == 1)
            return mas[0];
        else if(mas.length > 1){
            int x = mas[0];
            int[] mas2 = new int[mas.length-1];
            for(int i=1;i<mas.length;i++){
                mas2[i-1] = mas[i];
            }
            mas = mas2;
            return x;
        }
        else{
            return -1;
        }
    }

    public int Peek(){
        if(mas.length > 0)
            return mas[0];
        else
            return -1;
    }

    public int Count(){
        if(mas != null)
            return mas.length;
        else
            return 0;
    }

    public void Print(){
        for(int i=0;i<mas.length;i++){
            System.out.println(mas[i]);
        }
    }



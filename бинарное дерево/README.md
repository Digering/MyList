в данной программе было реализовано бинарное дерево используешее список для горизонтального выведения всего дерева

public class Main {

    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        tree.Add(8);
        tree.Add(5);
        tree.Add(10);
        
        tree.Print();
        System.out.println(" ");
        
        if(tree.Count() == 3){
            tree.Add(14);
            tree.Add(9);
            tree.Add(2);
            tree.Add(7);
            tree.Add(6);
        }
        
        tree.Print();
        System.out.println(" ");

        if(tree.Contains(6)){
            tree.Remove(6);
        }
        
        tree.Print();
        System.out.println(" ");

        tree.Clear();
        
        tree.Print();
        System.out.println(" ");


    }

Класс реализующий бинарное дерево

public class BinaryTree {

    public Tree root;
    static public Tree Newpos;
    public int num = 0;
    public BinaryTree(){}

    public static class Tree{

        int trunk;
        Tree left_branch;
        Tree right_branch;

        public Tree(int data){
            trunk = data;
            left_branch = null;
            right_branch = null;
        }

    }

    public void Add(int x){
        Tree Newroot = new Tree(x);
        num ++;
        if(root == null)
            Newpos = root = Newroot;
        else
        {
            Tree Newposs = root;
            while(true) {
                if(Newposs.trunk > x)
                    if(Newposs.left_branch == null){
                        Newposs.left_branch = Newroot;
                        break;
                    }
                    else
                        Newposs = Newposs.left_branch;
                else if(Newposs.trunk < x)
                    if(Newposs.right_branch == null){
                        Newposs.right_branch = Newroot;
                        break;
                    }
                    else
                        Newposs = Newposs.right_branch;
                else
                    break;
            }
        }
    }

    public void Vozvrat(){
        Newpos = root;
        System.out.println(Newpos.trunk);
    }
    public void PrintLeft(){
        if(Newpos.left_branch != null){
            Newpos = Newpos.left_branch;
            System.out.println(Newpos.trunk);
        }else
            System.out.println("NULL");
    }
    public void PrintRight(){
        if(Newpos.right_branch != null){
            Newpos = Newpos.right_branch;
            System.out.println(Newpos.trunk);
        }else
            System.out.println("NULL");
    }
    public void Remove(int x){
        Tree Newposs = root;
        boolean y = false;
        boolean z = true;
        Tree Newposs_2 = root;
        while (true) {
            if (Newposs.trunk == x) {
                z = false;
                if (Newposs.right_branch == null && Newposs.left_branch != null){
                    if(root.trunk == Newposs.trunk)
                        root = Newposs.left_branch;
                    else if(Newposs_2.left_branch.trunk == Newposs.trunk){
                        Newposs_2.left_branch = Newposs.left_branch;
                    }else if(Newposs_2.right_branch.trunk == Newposs.trunk){
                        Newposs_2.right_branch = Newposs.left_branch;
                    }
                } else if (Newposs.right_branch != null && Newposs.right_branch.left_branch == null) {
                    if(root.trunk == Newposs.trunk){
                        if(root.left_branch != null){
                            Newposs.left_branch = root.left_branch;
                        }
                        root = Newposs.right_branch;
                    }else if (Newposs_2.left_branch.trunk == Newposs.trunk) {
                        if(Newposs.left_branch != null)
                            Newposs_2.left_branch.right_branch.left_branch = Newposs.left_branch;
                        Newposs_2.left_branch = Newposs.right_branch;
                    }else if (Newposs_2.right_branch.trunk == Newposs.trunk) {
                        if(Newposs.left_branch != null)
                            Newposs_2.right_branch.right_branch.left_branch = Newposs.left_branch;
                        Newposs_2.right_branch = Newposs.right_branch;
                    }
                } else if (Newposs.right_branch != null) {
                    Tree New = root;
                    Newposs = Newposs.right_branch;
                    while (Newposs.left_branch != null){
                        New = Newposs;
                        Newposs = Newposs.left_branch;
                    }
                    if(root.trunk == Newposs.trunk){
                        Newposs.right_branch = root.right_branch;
                        Newposs.left_branch = root.left_branch;
                        root = Newposs;
                    } else if(Newposs_2.trunk > x){
                        if(Newposs_2.left_branch.left_branch != null){
                            Newposs.left_branch = Newposs_2.left_branch.left_branch;
                        }
                        Newposs.right_branch = Newposs_2.left_branch.right_branch;
                        Newposs_2.left_branch = Newposs;
                    } else if(Newposs_2.trunk < x){
                        if(Newposs_2.right_branch.left_branch != null){
                            Newposs.left_branch = Newposs_2.right_branch.left_branch;
                        }
                        Newposs.right_branch = Newposs_2.right_branch.right_branch;
                        Newposs_2.right_branch = Newposs;
                    }
                    if(New.left_branch.right_branch == null)
                        New.left_branch = null;
                    else
                        New.left_branch = New.left_branch.right_branch;
                }
                break;
            } else {
                if(Newposs.trunk > x){
                    if(Newposs.left_branch != null){
                        if(y && z)
                            Newposs_2 = Newposs;
                        Newposs = Newposs.left_branch;
                        y = true;
                    } else
                        break;
                } else{
                    if(Newposs.right_branch != null){
                        if(y && z)
                            Newposs_2 = Newposs;
                        Newposs = Newposs.right_branch;
                        y = true;
                    }else
                        break;
                }
            }
        }
    }

    public void Print(){
        int x= 0;
        Tree Newposs = root;
        Queue queue = new Queue();
        while (true){
                if(Newposs != null){
                    if(Newposs.left_branch != null){
                        queue.Add(Newposs.left_branch);
                    }else{
                        queue.Add(null);
                    }
                    if(Newposs.right_branch != null){
                        queue.Add(Newposs.right_branch);
                    }else{
                        queue.Add(null);
                    }
                    if(x == 0 || x == 2 || x == 6 || x == 14 || x == 16 || x == 32){
                        System.out.println(Newposs.trunk+" ");
                    }else{
                        System.out.print(Newposs.trunk+" ");
                    }
                }else{
                    if(x == 0 || x == 2 || x == 6 || x == 14 || x == 16 || x == 32){
                        System.out.println("NULL"+" ");
                    }else{
                        System.out.print("NULL"+" ");
                    }
                }
            if(queue.head == null){
                break;
            }
                Newposs = queue.Edit();
            x++;
        }
    }
    public int Count() {
        return num;
    }
    public void Clear(){
        root = null;
    }
    public boolean Contains(int x){
        boolean y = true;
        if(root == null)
            y = false;
        else
        {
            Tree Newposs = root;
            while(true) {
                if(Newposs.trunk > x)
                    if(Newposs.left_branch == null){
                        y = false;;
                        break;
                    }
                    else
                        Newposs = Newposs.left_branch;
                else if(Newposs.trunk < x)
                    if(Newposs.right_branch == null){
                        y = false;;
                        break;
                    }
                    else
                        Newposs = Newposs.right_branch;
                else
                    break;
            }
        }
        return y;
    }

Класс реализующий список

class Queue{

    public Och head;
    public static class Och{

        BinaryTree.Tree x;
        Och email;
        public Och(BinaryTree.Tree x){
            this.x = x;
            email = null;
        }
    }
    public void Add(BinaryTree.Tree x){
        Och Poss = new Och(x);
        if(head == null){
            head = Poss;
        }else{
            Och Poss_2 = head;
            while (true){
                if(Poss_2.email == null){
                    Poss_2.email = Poss;
                    break;
                }else{
                    Poss_2 = Poss_2.email;
                }
            }
        }

    }
    public BinaryTree.Tree Edit(){
        BinaryTree.Tree Poss_2 = null;
        if(head != null){
            Poss_2 = head.x;
            if(head.email != null) {
                head = head.email;
            }else{
                head = null;
            }
        }
        return Poss_2;
    }

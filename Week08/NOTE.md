  Bubblesort + Selectionsort + Insertionsort
    
    public class Practice {
    public int[] bubblesort(int[] arr){
        int n = arr.length;
        for(int i=0;i<n;i++){
            for(int j=0;j<n-(i+1);j++){
                if(arr[j]>arr[j+1]){
                    int tmp=arr[j];
                    arr[j]=arr[j+1];
                    arr[j+1]=tmp;
                }
            }
        }
        return arr;
    }
    public int[] selectionsort(int[] arr){
        int n = arr.length;
        for(int i=0;i<n-1;i++){
            int minindex=i;
            for(int j=i+1;j<n;j++){
                if(arr[j]<arr[minindex]) minindex=j;
            }
            int tmp=arr[i];
            arr[i]=arr[minindex];
            arr[minindex]=tmp;

        }
        return arr;
    }
    public int[] insertionsort(int[] arr){
        int n = arr.length;
        for(int i=1;i<n;i++){
            int pre=i-1;
            int cur=arr[i];
            while(pre>=0 && arr[pre]>cur) {
                arr[pre + 1] = arr[pre];
                pre--;
            }
            arr[pre+1]=cur;
        }
        return arr;
    }

    public static void main(String[] args) {

        Practice p=new Practice();
        int[] arr={91,60,96,13,35,65,46,65,10};
        int[] bubblesort = p.bubblesort(arr);
        int[] insertionsort = p.insertionsort(arr);
        int[] selectionsort = p.selectionsort(arr);
        for (int i : selectionsort) {
            System.out.printf(" "+i+" ");
        }
        System.out.println("\n");
        for (int i : insertionsort) {
            System.out.printf(" " + i+" ");
        }
        System.out.println("\n");
        for (int i : bubblesort) {
            System.out.printf(" "+i+" ");
        }

    }
    }

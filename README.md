import java.util.*;

// Matrix 2D- Array
public class Main
{
    
    static void display(int[][] arr){
        for(int i=0;i<arr.length;i++){
            
            for(int j=0;j<arr[0].length;j++){
                System.out.print(arr[i][j]+" ");
            }
            System.out.println();
        }
    }
    
    
    public static int find_sum(int[][] arr){
        int sum=0;
        
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                sum+=arr[i][j];
            }
        }
        
        return sum;
    }
    
    public static void multiple(int[][] arr1,int[][] arr2){
        
        int a1_row=arr1.length , a1_coloumn=arr1[0].length;
        int b1_row=arr2.length , b1_coloumn=arr2[0].length;
        
        if(a1_coloumn!=b1_row){
            System.out.println("Not vailid");
        }
        
        int[][] ans=new int[a1_row][b1_coloumn];
        
        for(int i=0;i<ans.length;i++){
            
            for(int j=0;j<ans[0].length ;j++){
                
                // we take any one a1_coloumn or b1_row
                
                for(int k=0;k< a1_coloumn;k++){
                    
                    ans[i][j] += arr1[i][k] * arr2[k][j] ;
                }
            }
        }
        
        
        for(int i=0;i<ans.length;i++){
            
            for(int j=0;j<ans[0].length ;j++){
                
               System.out.print(ans[i][j]+" ");
            }
            
            System.out.println();
        }
        
        
    }
    
    public static void move_row_to_coloumn_and_coloumn_to_row(int[][] arr){
        
        for(int i=0;i<arr[0].length;i++){
            for(int j=i;j<arr.length;j++){
                
                int temp=arr[i][j];
                arr[i][j]=arr[j][i];
                arr[j][i]=temp;
            }
        }
        
        display(arr);
    }
    
    public static void zigzag_row_wise(int[][] arr){
        int total=arr[0].length * arr.length;
        
        for(int i=0;i<arr.length;i++){
            if(i%2==0){
                for(int j=0;j<arr[0].length;j++){
                    System.out.print(arr[j][i]+" ");
                }
            }
            else{
                for(int j=arr.length-1;j>=0;j--){
                    System.out.print(arr[j][i]+" ");
                }
            }
            System.out.println();
        }
        
    }
    
    public static void spairal_traversal(int[][] arr){
        
        int minr=0,minc=0;
        int maxr=arr.length-1, maxc=arr[0].length-1;
        
        int total=arr.length * arr[0].length;
        int count=1;
        
        while(count<total){
            // top to buttom
            
            for(int i=minr ,j=minc;i<=maxr && count<total;i++){
                System.out.print(arr[i][j]+" ");
                count++;
            }
            minc++;
            //left to right
            
            for(int i=maxr,j=minc ;j<=maxc && count<total;j++){
                System.out.print(arr[i][j]+" ");
                count++;
            }
            maxr--;
            
            //buttom to up
            
            for(int i=maxr,j=maxc;i>=minr && count<total;i--){
                System.out.print(arr[i][j]+" ");
                count++;
            }
            maxc--;
            
            //right to left
            
            for(int i=minr,j=maxc;j>=minc && count<total;j--){
                System.out.print(arr[i][j]+" ");
                count++;
            }
            minr++;
        }
    }
    
    public static void exit_point(int[][] arr){
        
        int dir=0;
        int i=0,j=0;
        
        while(true){
            
            dir= (arr[i][j] + dir)%4;
            
            if(dir==0){
                j++;
            }
            else if(dir==1){
                i++;
            }
            else if(dir==2){
                j--;
            }
            else if(dir==3){
                i--;
            }
            
            if(i==-1){
                i++;
                break;
            }
            else if(j==-1){
                j++;
                break;
            }
            else if(i==arr[0].length){
                i--;
                break;
            }
            else if(j==arr.length){
                j--;
                break;
            }
            
        }
        
        System.out.print(i+" "+j);
    }
    
    static void rotate_by_90_degree(int[][] arr){
        
        // first we move_row_to_coloumn_and_coloumn_to_row matrix
        
        for(int i=0;i<arr[0].length;i++){
            for(int j=i;j<arr.length;j++){
                int temp=arr[i][j];
                arr[i][j]=arr[j][i];
                arr[j][i]=temp;
            }
        }
        
        
        // After that moving we 
        
        for(int i=0;i<arr.length;i++){
            
            int li=0;
            int ri=arr[i].length-1;
            
            while(li<ri){
                int temp=arr[i][li];
                arr[i][li]=arr[i][ri];
                arr[i][ri]=temp;
                li++;
                ri--;
            }
        }
        
        display(arr);
    }
    
    static void diagonal_traversal(int[][] arr){
        
        for(int i=0;i<arr.length;i++){
            int k=0;
            for(int j=i;j<arr.length;j++){
                System.out.print(arr[k][j]+" ");
                k++;   
            }
        }
    }
    
	public static void main(String[] args) {
		int[][] arr1={{1,2,3,4},{5,6,7,8},{9,1,1,2},{3,1,5,1}};
		int[][] arr2={{0,0,0,1},{0,0,0,0},{1,0,0,1},{0,1,1,0}};
		
	         //	display(arr1);
		     //System.out.println(find_sum(arr1));
		
	        //multiple(arr1,arr2);
	   
	       //move_row_to_coloumn_and_coloumn_to_row(arr1);
	        
	       // zigzag_row_wise(arr1);
	       
	       //spairal_traversal(arr1);
	       
	       //exit_point(arr2);
	       
	       //display(arr1);
	       
	       //System.out.println("\n\n\n");
	       
	       //rotate_by_90_degree(arr1); 
	       
	   //ye question phr se karna hai     // Shell rotate 
	   
	   diagonal_traversal(arr1);
	       
	       
	   
	}
}

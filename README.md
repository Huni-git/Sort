# Sort

## 코드

```java
//삽입정렬
public class insertsort {
	public void Sort(int[] arr){
		int size=arr.length; //배열의 길이
		int temp=0;          //인덱스 초기화 및 변수 선언
		int j;
		//삽입정렬의 과정
		for(int i=1;i<size;i++) {
			temp=arr[i];
			for(j=i-1;j>=0&&temp<arr[j];j--) {
				arr[j+1]=arr[j];
			}
			arr[j+1]=temp;
		}
	}
	
	public static void main(String [] args) {
		insertsort insort= new insertsort();
		int [] a= {3,6,2,7,4,1,5,9,8};
		insort.Sort(a);
		for(int i=0;i<a.length;i++) {
			System.out.println("a["+i+"]:"+a[i]);
		}
	}
}

//버블정렬
public class bubbleSort {
	public static void bubble(int[] arr) {
		
		//bubble 정렬의 과정
		for(int i=0;i<arr.length;i++) {
			for(int j=0;j<arr.length-i-1;j++) {
				if(arr[j]>arr[j+1]) {
					int temp = arr[j+1];
					arr[j+1]=arr[j];
					arr[j]=temp;
				}
			}
		}
	}
	public static void main(String[] args) {
		int [] a=new int []{3,6,2,7,4,1,5,9,8};
		bubbleSort bubble=new bubbleSort();
		bubbleSort.bubble(a);
		for(int i: a) {
			System.out.print(i+" ");
		}
	}
}

//선택정렬
public class selectionSort {
	public static void selectionsort(int []arr,int size) {
		for(int i=0; i<size;i++) {
			int min_index=i;
			for(int j=i+1;j<size;j++) {
			if(arr[j]<arr[min_index]) {
				min_index=j;
			}
		}
			//min_index의 값과 i번째 값 서로 교환,선택정렬
			swap(arr,min_index,i);
		}
	}
	
	//temp를 사용, 바꿔주는 메소드
	private static void swap(int[]a,int i,int j) {
		int temp=a[i];
		a[i]=a[j];
		a[j]=temp;
	}

	public static void main(String[]args) {
		int []a= {3,6,2,7,4,1,5,9,8};
		selectionSort.selectionsort(a,a.length);
		for(int i: a) {
			System.out.print(i+" ");
		}
	}
}
```

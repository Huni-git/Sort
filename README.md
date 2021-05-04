# Sort

## 정렬 설명
삽입 정렬(揷入整列, insertion sort)은 자료 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분과 비교하여, 자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘이다.

거품 정렬( - 整列, 영어: bubble sort, sinking sort)은 두 인접한 원소를 검사하여 정렬하는 방법이다.

선택 정렬(選擇整列, selection sort)은 제자리 정렬 알고리즘의 하나로, 다음과 같은 순서로 이루어진다. 주어진 리스트 중에 최소값을 찾는다. 그 값을 맨 앞에 위치한 값과 교체한다(패스(pass)). 맨 처음 위치를 뺀 나머지 리스트를 같은 방법으로 교체한다.

셸 정렬(영어: shell sort)은 주어진 자료 리스트를 특정 매개변수 값의 길이를 갖는 부파일(subfile)로 쪼개서, 각 부파일에서 정렬을 수행한다. 즉, 매개변수 값에 따라 부파일(Subfile)이 발생하며, 매개변수값을 줄이며 이 과정을 반복하고 결국 매개변수 값이 1이면 정렬은 완성된다.
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

//쉘정렬
import java.util.Arrays;
public class shellSort {
	public static void main(String[] args) {
		int[] a= {8,6,2,5,1,3,7,4};
		int size=a.length;
		shell(a,size);
	}
	//쉘 정렬, 간격 나누고 반복하는 과정
	public static void shell(int[] arr,int size) {
		System.out.println("정리되지 않은 배열"+Arrays.toString(arr));
		int interval=size/2;
		while(interval>=1) {
			for(int i=0;i<interval;i++) {
				insertSort(arr,i,size-1,interval);
			}
			System.out.println("간격="+interval);
			if(interval==1) {
				System.out.println("쉘정렬의 결과");
			}
			for(int j=0;j<size;j++) {
				System.out.print(arr[j]+" ");
			}
			System.out.println();
			interval=interval/2;
		}
	}
	//쉘정렬로 간격 구분 후, 삽입 정렬 실행.
	public static void insertSort(int arr[],int start,int fin,int interval) {
		int j=0;
		for(int i=start+interval;i<=fin;i=i+interval) {
			int box= arr[i];
			for(j=i-interval;j>=start&&box<arr[j];j=j-interval) {
				arr[j+interval]=arr[j];
			}
			arr[j+interval]=box;
		}
	}
}

```
## 코드 결과

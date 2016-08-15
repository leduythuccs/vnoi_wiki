# Thuật toán sắp xếp

# Giới thiệu

Ứng dụng về sắp xếp có ở khắp mọi nơi:

- Một danh sách lớp với các học sinh được sắp xếp theo thứ tự bảng chữ cái.
- Một danh bạ điện thoại.
- Danh sách các truy vấn được tìm kiếm nhiều nhất trên Google.

Thuật toán sắp xếp cũng được dùng kết hợp với những thuật toán khác, như tìm kiếm nhị phân, thuật toán Kruskal để tìm cây khung nhỏ nhất của đồ thị.

Vì sao chúng ta phải học nhiều thuật toán sắp xếp? Khi code, bạn chỉ cần biết cài một thuật toán sắp xếp là đủ. Hoặc nếu bạn code C++ hay Java, bạn chỉ cần biết cách gọi thư viện. Tuy nhiên, các thuật toán sắp xếp khác nhau cho ta nhiều ý tưởng hay và độc đáo - điều này vô cùng hữu ích khi các bạn học các thuật toán khác.

# Những điểm cần chú ý

Hãy thử tưởng tượng bạn có một bộ bài đã được xáo, và bạn muốn sắp xếp lại các lá bài theo thứ tự tăng dần. Bạn sẽ làm như nào? Có rất nhiều cách tiếp cận khác nhau:

- Chia bộ bài theo giá trị: 2, 3, 4... Rồi gộp lại.
- Trải tất cả các lá bài ra, rồi lần lượt lấy lá bài nhỏ nhất.
- Chia bộ bài ra thành nhiều nhóm nhỏ. Với mỗi nhóm, sắp xếp lại, sau đó gộp các nhóm lại với nhau theo thứ tự tăng dần.

Bạn sẽ thấy những cách tiếp cận khác nhau sẽ có thời gian nhanh chậm khác nhau. Các thuật toán sắp xếp cũng vậy. Có rất nhiều cách tiếp cận, với ưu, nhược điểm khác nhau.

Khi so sánh giữa các thuật toán này với nhau, có nhiều vấn đề phải quan tâm.

1. **Thời gian** chạy. Đối với các dữ liệu rất lớn, các thuật toán không hiệu quả sẽ chạy rất chậm và không thể ứng dụng trong thực tế.
2. **Bộ nhớ**. Các thuật toán nhanh đòi hỏi đệ quy sẽ có thể phải tạo ra các bản copy của dữ liệu đang xử lí. Với những hệ thống mà bộ nhớ có giới hạn (ví dụ embedded system), một vài thuật toán sẽ không thể chạy được.
3. **Độ ổn định** (**stability**). Độ ổn định được định nghĩa dựa trên điều gì sẽ xảy ra với các phần tử có giá trị giống nhau.
	- Đối với thuật toán sắp xếp ổn định, các phần tử bằng với giá trị bằng nhau sẽ giữ nguyên thứ tự trong mảng trước khi sắp xếp.
	- Đối với thuật toán sắp xếp không ổn định, các phần tử có giá trị bằng nhau sẽ có thể có thứ tự bất kỳ.

Trong bài viết này, ta giả sử cần sắp xếp tăng dần các phần tử. Để sắp xếp giảm dần, ta có nhiều cách:

- Sửa đổi thuật toán một cách phù hợp.
- Sắp xếp, sau đó đảo ngược thứ tự các phần tử.
- Định nghĩa lại việc so sánh nhỏ hơn.

# Sắp xếp nổi bọt (Bubble sort)

Đây là thuật toán cơ bản nhất cho việc sắp xếp.

## Ý tưởng

- Xét lần lượt các cặp 2 phần tử liên tiếp. Nếu phần tử đứng sau nhỏ hơn phần tử đứng trước, ta đổi chỗ 2 phần tử. Nói cách khác, phần tử nhỏ nhất sẽ **nổi** lên trên.
- Lặp lại đến khi không còn 2 phần tử nào thỏa mãn. Có thể chứng minh được số lần lặp không quá $N - 1$, do một phần tử chỉ có thể **nổi** lên trên không quá $N-1$ lần.

## Ưu điểm

- Code đơn giản, dễ hiểu
- Không tốn thêm bộ nhớ

## Nhược điểm

- Độ phức tạp $\mathcal{O}(N^2)$, không đủ nhanh với dữ liệu lớn.

## Code

```cpp
for (int i = 0; i < n; i++)
	for (int j = 0; j < n - 1; j++)
		if (a[j] > a[j+1]) {
			swap(a[j], a[j+1]);
		}
```

## Minh họa

Bạn có thể vào [VisuAlgo](http://visualgo.net/sorting).

- Chọn **Bubble** ở thanh menu bên trên.
- Ấn vào nút `Create` ở phía dưới trang để tạo một dãy mới
- Ấn vào `Sort`, rồi `Go` để chạy thuật toán.

# Sắp xếp chèn (Insertion Sort)

## Ý tưởng

Ý tưởng chính của thuật toán là ta sẽ sắp xếp lần lượt từng đoạn gồm 1 phần tử đầu tiên, 2 phần tử đầu tiên, ..., $N$ phần tử.

Giả sử ta đã sắp xếp xong $i$ phần tử của mảng. Để sắp xếp $i+1$ phần tử đầu tiên, ta tìm vị trí phù hợp của phần tử thứ $i+1$ và "chèn" nó vào đó.

## Ưu điểm

- Nếu danh sách đã gần đúng thứ tự, Insertion Sort sẽ chạy rất nhanh. Ví dụ bạn cần sắp xếp Highscore trong game.

## Nhược điểm

- Độ phức tạp $\mathcal{O}(N^2)$, không đủ nhanh với dữ liệu lớn.

## Code

```cpp
for (int i = 1; i < n; i++) {
	// Tìm vị trí phù hợp cho i
	int j = i;
	while (j > 0 && data[i] < data[j-1]) --j;

	// Đưa i về đúng vị trí
	int tmp = data[i];
	for (int k = i; k > j; k--)
		data[k] = data[k-1];
	data[j] = tmp;
}
```

## Minh họa

Bạn có thể vào [VisuAlgo](http://visualgo.net/sorting).

- Chọn **Insert** ở thanh menu bên trên.
- Ấn vào nút `Create` ở phía dưới trang để tạo một dãy mới
- Ấn vào `Sort`, rồi `Go` để chạy thuật toán.

# Sắp xếp trộn (Merge sort)

Sắp xếp trộn hoạt động như đệ quy. Đầu tiên chia nửa dữ liệu, và sắp xếp từng cái riêng biệt nhau. Sau đó phần tử đầu tiên một trong hai phần đó sẽ được so sánh. Các phần tử tiếp theo thực hiện tương tự cho tới khi được một danh sách hoàn chỉnh.

**Code:**

```cpp
int[] mergeSort (int[] data) {
   if (data.Length == 1)
      return data;
   int middle = data.Length / 2;
   int[] left = mergeSort(subArray(data, 0, middle - 1));
   int[] right = mergeSort(subArray(data, middle, data.Length - 1));
   int[] result = new int[data.Length];
   int dPtr = 0;
   int lPtr = 0;
   int rPtr = 0;
   while (dPtr < data.Length) {
      if (lPtr == left.Length) {
         result[dPtr] = right[rPtr];
         rPtr++;         
      } else if (rPtr == right.Length) {
         result[dPtr] = left[lPtr];
         lPtr++;
      } else if (left[lPtr] < right[rPtr]) {
         result[dPtr] = left[lPtr];
         lPtr++;
      } else {
         result[dPtr] = right[rPtr];
         rPtr++;         
      }
      dPtr++;
   }
   return result;
}
```

Mỗi lần gọi đệ quy mất $O(n)$, và tổng cộng cần $O(log{n})$ như vậy, do đó độ phức tạp thuật toán là $O(n*log{n})$. Thuật toán này có thể được cải thiện để sắp xếp một danh sách gần như đúng thứ tự. Sau khi đã sắp xếp từng nửa danh sách, nếu phần tử cao nhất của phần này nhỏ hơn phần tử nhỏ nhất của phần kia, thủ tục trộn không cần thiết nữa. (Ví dụ là phần Java API là phần cải tiến thuật toán này). Dữ liệu, qua từng lời đệ quy, sẽ như thế này:

```
{18, 6, 9, 1, 4, 15, 12, 5, 6, 7, 11}
{18, 6, 9, 1, 4} {15, 12, 5, 6, 7, 11}
{18, 6} {9, 1, 4} {15, 12, 5} {6, 7, 11}
{18} {6} {9} {1, 4} {15} {12, 5} {6} {7, 11}
{18} {6} {9} {1} {4} {15} {12} {5} {6} {7} {11}
{18} {6} {9} {1, 4} {15} {5, 12} {6} {7, 11}
{6, 18} {1, 4, 9} {5, 12, 15} {6, 7, 11}
{1, 4, 6, 9, 18} {5, 6, 7, 11, 12, 15}
{1, 4, 5, 6, 6, 7, 9, 11, 12, 15, 18}
```

Ngoài việc hiệu quả, sắp xếp trộn còn có thể giúp giải các bài toán khác, chẳng hạn như xác định "danh sách đã sắp xếp".

# Sắp xếp vun đống

Trong sắp xếp vun đống, ta tạo một cấu trúc heap từ dữ liệu. Cấu trúc heap là cấu trúc lưu dữ liệu sao cho phần tử nhỏ nhất (hoặc lớn nhất) luôn ở nút gốc. (Heap còn được gọi là hàng đợi ưu tiên, xem qua [Data Structures](http://community.topcoder.com/tc?module=Static&d1=tutorials&d2=dataStructures)). Để thực hiện, dữ liệu được đưa vào heap và nút gốc được thay thế liên tục. Từ khi nút gốc là phần tử nhỏ nhất, kết quả là một danh sách đã sắp xếp. Nếu bạn đã có code Heap haowjc bạn dùng Java PriorityQueue (điểm mới trong bản 1.5), code thuật toán này khá ngắn.

**Code:**

```cpp
Heap h = new Heap();
for (int i = 0; i < data.Length; i++)
   h.Add(data[i]);
int[] result = new int[data.Length];
for (int i = 0; i < data.Length; i++)
   data[i] = h.RemoveLowest();
```

Độ phức tạp thuật toán này là giới hạn trên của $O(n*log{n})$. Ngoài ra, thuật toán này yêu cầu thêm bộ nhớ là kích cỡ của dữ liệu. Sắp xếp vun đống có điểm yếu là không ổn định, và khó hiểu hơn các thuật toán sắp xếp cơ bản.

# Sắp xếp nhanh

Như tên gọi, đây là một thuật toán rất hiệu quả. Cấu trúc đằng sau nó là cách mà con người thường hay sắp xếp. Đầu tiên chia thành hai nhóm, nhóm các phần tử "lớn" và nhóm các phần tử "nhỏ". Sau đó, gọi đệ quy hai nhóm.

**Code:**

```cpp
Array quickSort(Array data) {
   if (Array.Length <= 1)
      return;
   middle = Array[Array.Length / 2];
   Array left = new Array();
   Array right = new Array();
   for (int i = 0; i < Array.Length; i++)
      if (i != Array.Length / 2) {
         if (Array[i] <= middle)
            left.Add(Array[i]);
         else
            right.Add(Array[i]);
      }
   return concatenate(quickSort(left), middle, quickSort(right));
}
```

Thách thức trong sắp xếp nhanh là xác định phần tử khóa làm mốc chia thành hai nhóm. Độ phức tạp thuật toán này phụ thuộc vào chọn phần tử đó chính xác như thế nào. Trong trường hợp tốt nhất, độ phức tạp là $O(n*log{n})$, và xấu nhất đối với hai tập có cùng một phần tử là $O(n^{2})$. Dữ liệu sẽ thay đổi như sau:

```
{18, 6, 9, 1, 4, 15, 12, 5, 6, 7, 11}
{6, 9, 1, 4, 12, 5, 6, 7, 11} {15} {18}
{6, 9, 1, 4, 5, 6, 7, 11} {12} {15} {18}
{1, 4} {5} {6, 9, 6, 7, 11} {12} {15} {18}
{1} {4} {5} {6} {6} {9, 7, 11} {12} {15} {18}
{1} {4} {5} {6} {6} {7} {9, 11} {12} {15} {18}
{1} {4} {5} {6} {6} {7} {9} {11} {12} {15} {18}
```

Nếu biết rõ các phần tử cần sắp xếp thuộc phần nào nhất định, bạn có thể cải thiện thuật toán bằng cách chọn phần tử khóa chia dữ liệu thành hai tập chính xác nhất có thể. Cải tiến chung là chọn phần tử khóa chú ý đến giới hạn các phần tử hoặc random.

# Sắp xếp cơ số

Thuật toán này được thiết kế sao cho vẫn sắp xếp nhưng không so sánh trực tiếp các phần tử. Đầu tiên, thuật toán sẽ lấy các chữ số cuối (hoặc nhiều chữ số, các bit), và đưa các phần tử vào các nhóm. Nếu ta lấy 4 bit một lúc, ta cần 16 nhóm. Sau đó ta đưa các nhóm lại với nhau, và được danh sách sắp xếp theo chữ số cuối của các phần tử. Quá trình này lặp đi lặp lại với chữ số át cuối cho tới khi tất cả vị trí chữ số đã sắp xếp.

Lấy ví dụ, hãy xem qua một dãy các số sắp xếp bằng cách lấy 1 bit. Lưu ý rằng, chúng ta tốn 4 bước để có được kết quả, và mỗi bước ta dùng đúng 2 nhóm:

```
{6, 9, 1, 4, 15, 12, 5, 6, 7, 11}
{6, 4, 12, 6} {9, 1, 15, 5, 7, 11}
{4, 12, 9, 1, 5} {6, 6, 15, 7, 11}
{9, 1, 11} {4, 12, 5, 6, 6, 15, 7}
{1, 4, 5, 6, 6, 7} {9, 11, 12, 15}
```

Lấy 2 bit, chúng ta cần 2 bước và 4 nhóm:

```
{6, 9, 1, 4, 15, 12, 5, 6, 7, 11}
{4, 12} {9, 1, 5} {6, 6} {15, 7, 11}
{1} {4, 5, 6, 6, 7} {9, 11} {12, 15}
```

Lấy 4 bit và chỉ cần 1 bước, cùng 16 nhóm:

```
{6, 9, 1, 4, 15, 12, 5, 6, 7, 11}
{1} {} {} {4} {5} {6, 6} {7} {} {9} {} {11} {12} {} {} {15}
```

Chú ý rằng, với ví dụ cuối, ta có nhiều nhóm rỗng. Điều này giải thích rằng, ta có bao nhiêu bit ta có thể chọn hơn trước khi dùng đến giới hạn bộ nhớ. Thời gian thực hiện giống như số các xô càng lớn đưa thành một danh sách có thể đôi lúc phải xem xét.

Bởi vì hiệu quả sắp xếp cơ số khác với sắp xếp so sánh bình thường, nó có thể có hiệu quả cao hơn nữa. Độ phức tạp là $O(n*{k})$ với k là kích cỡ của khóa. (số nguyên 32 bit, nếu lấy 4 bit, k=8). Điểm yếu cơ bản là một vài dữ liệu rất dài (như chuỗi), hoặc khó dùng thuật toán này (chẳng hạn kiểu negative floating-point là một ví dụ).

# Các thư viện dùng để sắp xếp

Ngày nay, đại đa số các ngôn ngữ lập trình đã bao gồm nhiều thư viện cung cáp các thuật toán tốt cho chúng ta. Như .NET framework, Java API, và C++ STL, tất cả đều đã có sẵn thuật toán sắp xếp. Và tốt nhất là cấu trúc cơ bản của nó giống nhau từ ngôn ngữ này đến ngôn ngữ khác.

Với các kiểu dữ liệu điển hình như scalars, floats, chuỗi, mọi thứ cần dùng để sắp xếp đã có sẵn. Nhưng nếu ta có dữ liệu cần thuật toán sắp xếp phức tạp hơn? Rất may, lập trình hướng đối tượng đã cho ta các thư viện kinh điển để giải quyết việc này.

Trong cả Java và C# (cũng như VB), có giao diện gọi là Comparable (IComparable in .NET). Bằng việc chạy giao diện IComparable trên một class đã khai báo, bạn thêm hàm ***int CompareTo (object other)***, hàm này sẽ trả về một kết quả, kết quả đó sẽ <=0, hoặc là một số dương lớn hơn tham số. Thư viện chứa hàm sort sẽ chạy tốt trên kiểu dữ liệu mới.

Ngoài ra, có một giao diện khác gọi là Comparator (IComparer in .NET), mà đã định nghĩa một hàm riêng biệt ***int Compare (object obj1, object obj2)***, nó sẽ trả về một giá trị chỉ ra kết quả của việc so sánh hai tham số.

Hạnh phúc nhất của các hàm sắp xếp được cung cấp trong thư viện là nó cứu ta rất nhiều thời gian khỏi việc code, đỡ rối hơn, không cần phải khó khăn nỗ lực. Tuy nhiên, dù tất cả mọi việc đã được chuẩn bị sẵn, biết được hoạt động của nó vẫn rất hay.

# Nguồn tham khảo

- [Topcoder](https://www.topcoder.com/community/data-science/data-science-tutorials/sorting/)
- [VisuAlgo](http://visualgo.net/sorting)
- [Wikipedia](http://en.wikipedia.org/wiki)
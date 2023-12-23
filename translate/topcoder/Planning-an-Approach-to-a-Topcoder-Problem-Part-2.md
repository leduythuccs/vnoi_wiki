# Những cách tiếp cận bài toán: Phần 2

Bài viết bởi [leadhyena_inran](https://www.topcoder.com/members/leadhyena_inran/).

Nguồn: [Topcoder](https://www.topcoder.com/community/data-science/data-science-tutorials/planning-an-approach-to-a-topcoder-problem-part-2/)

[[_TOC_]]

# Tiếp cận từ dưới lên (Bottom-up Programming)

Kỹ thuật này ngược với kỹ thuật chia nhỏ vấn đề đã được nói đến ở [bài viết trước](/translate/topcoder/Planning-an-Approach-to-a-Topcoder-Problem-Part-1), và nó nên là kỹ thuật đầu tiên bạn nghĩ tới khi bạn chưa tìm ra hướng giải. Bottom-up programming là phương pháp xuất phát từ những hàm cơ bản, chỉnh sửa, thêm tính năng, kết hợp chúng để giải được bài toán ban đầu. Nhiều lúc khi vừa đọc đề bạn sẽ thấy rằng bạn cần một hàm cụ thể nào đó để giải bài này, nếu nó đã atomic hay dễ dàng cài đặt thì bạn có thể có thể xây dựng thẳng lên từ những hàm cơ bản đó thay vì chia nhỏ ra.

Trong bài [MatArith](https://community.topcoder.com/stat?c=problem_statement&pm=511&rd=4335) ở phần trước, chương trình con để cộng và nhân ma trận cũng có thể áp dụng kĩ thuật này. Bạn có thể viết một hàm `evalMult` nhỏ hơn có nhiệm vụ nhân các ma trận với nhau bằng cách xử lí luôn trên string, một hàm `evalAdd` tương tự để cộng ma trận.

Nói chung, xây dựng dần dần lên những chương trình con trước khi giải quyết vấn đề chính của bài toán là một chiến thuật khá tốt. Một vài ví dụ điển hình là các thao tác trên cấu trúc dữ liệu (data structures), các toán tử của ma trận, số phức... Bạn sẽ thấy rằng, bằng việc giải quyết những vấn đề nhỏ trước, bạn sẽ hình dung rõ hơn bạn cần làm gì. Thỉnh thoảng, nếu bạn bị bế tắc với cách này, thì hãy viết một vài dòng atomic code để xem việc chia nhỏ vấn đề ra thì có hợp lí hơn hay không. Như bạn thấy, để tìm được cách tiếp cận đúng thì phải thử để biết cách tiếp cận nào sai trước đã.

Bên cạnh đó, hãy nhớ rằng bất kì dòng code nào bạn viết ra đều phải được kiểm tra kĩ trước khi xây dựng lên cao, bởi vì đây là những dòng code đầu tiên bạn viết và bạn sẽ chóng quên khi càng viết lên những phần phía trên. Một mẹo khá hay để tìm lỗi: nó thường nằm trong những dòng code cũ của bạn.


# Vét cạn (Brute Force)

Bất cứ khi nào đề bài yêu cầu một kết quả tối ưu, thì cách đơn giản nhất để giải quyết vấn đề là thử tất cả các trường hợp xảy ra. Bất cứ khi nào lời giải đòi hỏi việc tính toán nhiều bước, cách tốt nhất để giải là làm theo từng bước tính toán đó. Bất cứ khi nào bài toán yêu cầu bạn đếm những cách để làm một thứ gì đó trong một điều kiện cho trước, cách tốt nhất là thử tất cả mọi cách và chọn những cách thỏa yêu cầu. Nói cách khác, cách tiếp cận đầu tiên cho các bài toán nên là một cách dễ nhận thấy nhất, cho dù nó không phải là cách tốt nhất.

Chiến thuật tiếp cận này gọi là vét cạn (brute force) - xét qua tất cả các trường hợp có thể xảy ra để tìm kết quả. Mỗi khi bạn gặp một bài toán, đầu tiên phải xét đến là test xấu nhất có thể có là gì và liệu thời gian cho phép có đủ không. Nếu có thể, hãy brute force vì thường code sẽ đơn giản và ít mắc lỗi hơn. Bạn cũng phải có đủ kiến thức về môi trường lập trình (programming environment) để ước lượng thời gian chạy của chương trình. Có nhiều trường hợp do không ước lượng đúng nên đã bỏ qua cách brute force đơn giản và tốn thời gian vào debug những cách giải phức tạp, cũng tương tự như việc bị quá thời gian (time limit exceeded) khi không dự đoán được đến trường hợp xấu nhất.

Nói chung, nếu bạn không thể tìm ra được cách nào khác để giải, thì hãy dùng brute-force. Nếu không đủ nhanh, thì tiếp tục tìm cách khác tối ưu hơn. Sau đó chúng ta có thể sử dụng code brute-force để test cho những cách giải khác (vì code brute-force bao giờ khả năng mắc lỗi cũng thấp hơn).


# Sử dụng giải thuật

Sử dụng những giải thuật cơ bản cũng là cách tiếp hiệu quả. Việc này cũng giống như việc đi các nước mở đầu giống nhau khi chơi cờ vậy. Thông thường, cách thử lần lượt các thuật toán để tiếp cận bài toán là một cách làm không hay cho lắm (nó tạo ra tư duy lối mòn và nhiều lỗ hổng kiến thức cho các bài toán cơ bản), nhưng nó cũng không phải là một ý tồi nếu sử dụng nó như một atomic code hay dựa vào đó để chia nhỏ vấn đề ra.

Bài này mình không bàn luận nhiều về giải thuật (đã có nhiều bài hướng dẫn về phần này), mà bàn về việc nên dùng giải thuật như thế nào để xác định cách tiếp cận bài toán. Biết cách sử dụng giải thuật trong trường hợp cơ bản là chưa đủ, hãy cố gắng hiểu thật sâu về nó. Ví dụ, bài [CityLink SRM 170 Div I Med](http://topcoder.bgcoder.com/print.php?id=369), dùng kết hợp các giải thuật đồ thị (graph algorithm) đơn giản để giải, ngược lại việc code một giải thuật thông thường thì không đủ. Chỉ có hiểu sâu về cách hoạt động của thuật toán mới có thể tìm ra được cách kết hợp chúng với nhau.

Vì vậy, khi học một giải thuật mới, bạn phải hiểu được code chạy như thế nào, độ phức tạp là bao nhiêu, phần nào của code có thể thay đổi được và ảnh hưởng như thế nào đến thuật toán. Việc nhớ cách code một giải thuật cũng cực kì quan trọng, bởi vì nếu không có kinh nghiệm cài đặt thì sẽ rất khó để tìm lỗi. Sử dụng thuật toán một cách sáng tạo để giải quyết nhiều bài toán khác nhau cũng là một cách luyện tập hữu ích. Ít ra thì ta có thể biết được những trường hợp nào không phù hợp để dùng thuật toán này. Đó là lý do tại sao nên học những kĩ thuật nền tảng như chia để trị (divide-and-conquer), quy hoạch động (dynamic programming), tham lam (greedy algorithms) trước những thuật toán cụ thể khác, bởi vì những kĩ thuật đó có thể dễ dàng tùy biến một khi bạn đã hiểu cách hoạt động.


# Phát biểu lại bài toán theo cách khác

Tình huống này rất quen thuộc: bạn cảm thấy mình đuối sức bởi việc cố gắng tìm ra dạng bài của đề. Điều này xảy ra có lẽ vì đề bài cần phải biến đổi để tiếp cận được, khi biến đổi đề bài thì chúng ta sẽ dề dàng nhận ra vấn đề hơn. Ví dụ điển hình là bài [Game of Fifteen - SRM 172](https://community.topcoder.com/stat?c=problem_statement&pm=1850&rd=4665). Trong bài này, bạn có những con số từ 1 đến 9, bạn có thể lấy một trong những con số đó theo lượt, nếu bạn có 3 số trong các số bạn đã chọn có tổng bằng 15 trước đối thủ, bạn thắng. Với bài toán này, bạn có thể điều chỉnh lại đề bài bằng việc đặt các con số trong ma trận 3x3 (trong đó mỗi dòng, mỗi cột và đường chéo có tổng bằng nhau, trong trường hợp này là 15). Ngay lập tức bạn nhận ra rằng đây chỉ là trò chơi Tic-Tac-Toe. Việc thay đổi này đã biến một bài toán mà bạn chưa từng gặp, thành một bài toán bạn đã tiếp xúc nhiều hơn. Một số nhà toán học gọi nó là cách tiếp cận $ABA^{-1}$, bởi vì: đầu tiên bạn thay đổi dạng đề bài $(A)$, sau đó giải nó $(B)$, và trả ngược lại vấn đề ban đầu $A^{-1}$. Cách tiếp cận này rất phổ biến trong việc giải những bài toán phức tạp như [diagonalizing matrices](http://mathworld.wolfram.com/MatrixDiagonalization.html) và giải Rubik.

Cách tiếp cận này được phổ biến để làm đơn giản đi những phép toán cơ bản. Ví dụ: [HexagonIntersections - SRM 206](https://community.topcoder.com/stat?c=problem_statement&pm=2920&rd=5852&rm=&cr=10225719). Trong bài toán này, chúng ta cần tìm số hình 6 cạnh chạm một đường thẳng cho trước. Bài toán trở nên đơn giản hơn nếu bạn lật nghiêng cái lưới qua, nên những hình 6 cạnh có cạnh song song với trục x và y, bài toán vẫn giữ nguyên đáp án như cũ, nhưng đã đơn giản hơn nhiều.

Hãy chú ý đến lúc debug nếu bạn sử dụng phương pháp này. Nhớ rằng đáp án trả về là đáp án của bài toán đã bị biến đổi, bạn cần phải trả lại đáp án cho bài toán ban đầu. Để không phải quên, bạn nên để lại một vài comment ở phần đó.


# Gỡ bỏ những định nghĩa

Phương pháp này là một mẹo cũ của những nhà toán học, được giải quyết đối với những trường hợp đề bài được cho với hàng đống các định nghĩa chồng lên nhau, nó được sử dụng để tháo gỡ những rối rắm trong đề bài để tìm được cách tiếp cận thích hợp. Khi bạn đọc một định nghĩa nào đó mà bạn chưa bao giờ thấy trước đây, cố gắng nghĩ cách làm thế nào để code nó. Nếu chương trình yêu cầu bạn tìm ra một *grozmojt* đơn giản nhất trong tập số nguyên (ở đây *grozmojt* là một thuật ngữ không có thật để ví dụ về định nghĩa bạn chưa bao giờ thấy). Đầu tiên bạn phải tìm ra được làm sao để code của bạn nhận ra đó là một *grozmojt*, rồi sau đó tìm cách để tìm kiếm nó. Cách tiếp cận này rất giống với các tiếp cận từ dưới lên (bottom-up programming), nhưng làm việc trên định nghĩa thay vì trên các chương trình con.

Những bài toán mô phỏng cũng được sử dụng với các chiến thuật tương tự. Cách tốt nhất để làm những bài toán mô phỏng là tạo ra một đối tượng giống như vậy, có thể thực hiện các hành động được yêu cầu. Bằng cách đó, bạn sẽ không phải lo bạn có đưa đủ thông tin trạng thái vào các hàm hay không, bởi vì tất cả thông tin đã gói gọn trong đối tượng, cách tiếp cận này trở nên nên tiện lợi và code được atomic rất nhanh. Đây cũng là một cách tiếp cận đúng đắn nếu một thuật toán cần được mô phỏng để đếm số bước thực hiện (như MergeSort), hoặc là số đối tượng được giải phóng bộ nhớ trong các thuật toán khác (như ImmutableTrees). Trong những trường hợp như vậy, tính gọn gàng và đơn giản của code làm cho việc suy nghĩ các bước tiếp theo dễ dàng hơn.


# Bài toán có thể giải được

Có một bài toán về hình học như thế này: bạn được cho một cặp hình tròn đồng tâm và bạn chỉ có độ dài dây cung của hình tròn bên ngoài mà tiếp tuyến với hình tròn bên trong (kí hiệu là x). Bạn được hỏi là diện tích ở giữa 2 hình tròn là bao nhiêu. Bạn nghĩ rằng: “nếu bài này có thể giải được thì bán kính của đường tròn bên trong là không cần thiết với việc tính toán, nên mình sẽ đặt nó bằng 0. Bởi vì diện tích của hình tròn bên trong bằng 0, hoặc bị làm suy biến ở tâm của hình tròn bên ngoài, nên dây cung của hình tròn bên ngoài đi qua tâm, do đó đường kính và diện tích của hình tròn ngoài bằng $\pi(x/2)^{2}$”. Chú ý rằng việc chứng minh toán học đầy đủ của bài này thì khó hơn, nhưng sự thật là việc đáp án có tồn tại làm cho bài toán dễ hơn. Bởi vì người ra đề phải viết đáp án cho bài toán, bạn biết rằng các bài toán đó đều có thể giải được, đó cũng là một lợi thế lớn trong những contest của SRM.

Cách tiếp cận này cũng áp dụng được cho suy nghĩ rằng người ra đề sẽ tìm một dạng bài toán cụ thể nào đó, và thỉnh thoảng dựa vào việc chỉnh sửa đề bài gốc, ta được gợi ý hướng làm(đặc biệt trong trường hợp khi bài toán được xem là quá khó). Một vài ví dụ như xét qua các điều kiện ban đầu của đề bài như mảng chỉ có nhiều nhất 20 phần tử (mà rất nhiều coder có kinh nghiệm sẽ nói rằng tác giả muốn bạn sử dụng brute-force cho bài này), hay giới hạn số nguyên trong khoảng từ 1 đến 10000 (cho phép nhân các số với nhau mà không tràn). Bằng việc dựa vào các điều kiện giới hạn này của đề bài, bạn sẽ giới hạn lại được độ phức tạp của bài toán và tìm ra cách tiếp cận đơn giản và tốt hơn.

Thỉnh thoảng độ khó của bài toán cũng có thể gợi ý được cách giải nó. Ví dụ, bài [FanFailure - SRM 195 Div I](https://community.topcoder.com/stat?c=problem_statement&pm=2235&rd=5070&rm=&cr=274023). Bài toán liên quan đến tập hợp con (subsets), nhiều nhất (maximal) và ít nhất (minimal), nên bạn sẽ nghĩ rằng brute-force sẽ có tác dụng, rồi sau đó bạn thấy rằng mảng nhiều nhất đến 50 phần tử. $2^{50}$ tập con khác nhau sẽ làm bạn bỏ ngay cái ý tưởng brute-force (người ra đề chú trọng đến cách tư duy hơn là kĩ năng code), và tìm một cách tiếp cận khác... Nhưng khi bạn nhận ra đó là bài Div I Easy và nó cũng trông không đến nỗi khó như vậy, thì bạn sẽ nghĩ đến cách tham lam (greedy). Có thể bạn sẽ không rút ra được nhận xét đó nếu nó không phải là bài Div I Easy.

Hãy nhớ rằng đó chỉ là những mẹo nhỏ và không nên quan tâm nhiều đến việc tại sao nó hoạt động hay không, nó chỉ gợi ý cho ta biết rằng những gì người ra đề đang nghĩ. Hơn thế nữa, nếu người ra đề thuộc dạng người thích đánh đố, cân não người khác, thì cách này sẽ không thể dùng được. Miễn là bạn đưa ra cách tiếp cận dựa trên những lập luận logic thay vì đoán mò, thì đây cũng là một mẹo khá hữu ích.


# Chia trường hợp

Có một số bài được giải bằng việc chia bài toán theo từng trường hợp chứ không phải theo từng bước. Bằng cách chia nhỏ bài toán thành những trường hợp, với mỗi tập đầu vào khác nhau, bạn có thể viết một hàm con để giải quyết nó và đều đó hiển nhiên là dễ hơn. Xét bài [TeamPhoto - SRM 167 Div I Medium](https://community.topcoder.com/stat?c=problem_statement&pm=1614&rd=4640&rm=&cr=260214). Bài này chia trường hợp đơn giản nhưng rất khó để giải. Nếu bạn chia bài toán thành những trường hợp riêng, bạn sẽ thấy rằng bài toán ban đầu không thể giải được bài thuật toán tham lam, thì mỗi trường hợp của nó có thể, và bạn có thể chọn trường hợp tối ưu nhất để đưa ra đáp án.

Trường hợp thường dùng cách tiếp cận này nhất là khi cần phải bỏ đi những test ở biên, để chúng ta không phải thay đổi solution chính quá nhiều. Một ví dụ là bài [BirthdayOdds - SRM 174 Div I Easy](https://community.topcoder.com/stat?c=problem_statement&pm=1848&rd=4675&rm=&cr=272072), rất nhiều người dùng dòng này để xử lí `if (daysInYears == 1) return 2;` cho trường hợp biên. Để tránh những trường hợp như thế, chúng ta nên xét riêng nó ra. Bằng cách thêm vào các dòng code để kiểm tra những test ở biên, độ an toàn của solution được tăng lên, và dễ dàng hơn trong việc kiểm tra cách tiếp cận đó là đúng.


# Kế hoạch bên trong kế hoạch

Như đã nói phía trên, các cách tiếp cận một bài toán không dễ phân loại. Hơn nữa có nhiều bài phải kết hợp rất nhiều bước để đưa ra một đáp án hoàn chỉnh. Ví dụ như bài [MagicianTour - SRM 191 Div I Hard](https://community.topcoder.com/stat?c=problem_statement&pm=2346&rd=4775&rm=&cr=272072). Để giải được bài này cần phải làm 2 bước: bước đầu tiên cần việc tìm kiếm trên đồ thị để tìm những thành phần liên thông (connected components) và 2-coloring của nó (cách tô đồ thị chỉ bằng 2 màu), bước thứ hai phải dùng quy hoạch động giống bài toán balo. Trong những trường hợp như thế này, hãy nhớ rằng nhiều lúc sẽ cần phải áp dụng nhiều hơn một cách tiếp cận cho một bài toán. Một ví dụ khác là bài [TopographicalImage - SRM 210 Div II Hard](https://community.topcoder.com/stat?c=problem_statement&pm=2932), bài này yêu cầu tìm góc nhỏ nhất để tính giá trị cho đường đi ngắn nhất trong một giới hạn nhất định. Để giải quyết nó, chú ý rằng việc tìm giá trị nhỏ nhất có thể làm bằng chặt nhị phân (binary search), nhưng ta cũng cần phải suy nghĩ kĩ hơn nữa, phần kế hoạch bên trong là có thể áp dụng giải thuật Floyd-Warshall để xem góc đã thỏa mãn chưa.

Nhớ rằng một cách tiếp cận không phải chỉ là *“Ồ, mình biết cách chia nhỏ bài này ... Làm thôi!”*. Ý tưởng cho việc tìm cách tiếp cận là suy nghĩ, lập luận có kế hoạch về: các bước cần làm trong code của bạn, áp dụng thuật toán này như thế nào, làm thế nào để lưu và truyền giá trị các biến, code có pass được trường hợp xấu nhất không, nơi nào dễ sinh ra bug nhất. Nếu chúng ta lên kế hoạch kĩ càng thì khả nắng đúng càng cao hơn. Với mỗi cách tiếp cận thì phải có những bước lên kế hoạch cho cách tiếp cận đó.


# Thay đổi các cách tiếp cận

Không bao giờ có cách tiếp cận tốt nhất cho tất cả các coder, luôn luôn có ít nhất 2 cách để tiếp cận một vấn đề. Hãy xét bài [OhamaLow - SRM 206 Div I Easy](https://community.topcoder.com/stat?c=problem_statement&pm=2435&rd=5852&rm=&cr=10225719). Cách thông dụng hơn để tiếp cận bài này là thử tất cả các trường hợp xảy ra, với những cấu hình thỏa mãn yêu cầu thì sort lại và so sánh nó với đáp án để cập nhật lại đáp án. Đây là chiến thuật tìm kiếm vét cạn phổ biến nhất. Nhưng nó không chỉ có vậy, hãy nhớ rằng phải luôn có những phân tích nhỏ trong những phân tích lớn. Bạn phải tìm ra cách làm sao để tạo ra từng cấu hình (có thể cài bằng đệ quy hay sử dụng nhiều vòng lặp lồng nhau), làm thế nào để lưu những cấu hình lại (mảng, xâu, hay thậm chí dùng class) và làm thế nào để so sánh những cấu hình đó. Ở mỗi bước có rất nhiều cách để làm và hấu hết tất cả các cách làm đều chạy được. Như đã nói, có rất nhiều trường hợp ta tìm được nhiều cách xử lí khác nhau cho cùng một vấn đề. Ví dụ như bài toán yêu cầu bạn tìm một cấu hình thỏa mãn 2 điều kiện: điều kiện bắt buộc và điều kiện tối ưu. Thay vì tạo những cấu hình thỏa mãn điều kiện bắt buộc, rồi duyệt qua chọn cấu hình tối ưu nhất, ta có thể tạo ra tất cả các cấu hình, sắp xếp theo thứ tự từ tốt nhất đến xấu nhất, rồi chỉ cần chọn cấu hình đầu tiên thỏa mãn điều kiện bắt buộc. Nói cách khác, bạn lấy các xâu con 5 ký tự từ xâu "87654321" để xem shared hand và player hand có thể tạo thành chosen hand được không, nếu được thì trả lại về kết quả đó. Cách tiếp cận này cũng đòi hỏi những bước đi nhỏ (làm thế nào để kết hợp shared hand và player hand, làm thể nào để kiếm tra các cấu hình, vân vân) nhưng thỉnh thoảng (trường hợp này tốt hơn) bạn có thể chia nhỏ nó ra nhanh hơn.

Để có quyền chọn một trong hai cách tiếp cận, bạn phải nghĩ ra được cả hai. Cách luyện tập cho việc này là hãy tìm nhiều cách giải khác nhau của một bài toán (ví dụ như giải lại các bài SRM đã tham gia với cách giải khác). Bằng cách này, bạn sẽ tăng được khả năng tìm kiếm nhiều cách tiếp cận vấn đề, có thể đó là một cách tốt hơn, hay hơn, hay thậm chi là dễ debug hơn.


# Quay lui các cách tiếp cận sai

Như đã nói đến ở phần trước, một bài toán có rất nhiều cách tiếp cận là điều rất thường gặp. Bạn có thể chợt nghĩ đến nó khi đang code dang dở cách hiện tại. Một trong những kĩ năng khó để luyện tập nhất khi tham gia SRM đó là khả năng để hoàn toàn tập trung vào cách tiếp cận hiện tại, không bị phân tâm bởi có nhiều cách tiếp cận khác. Nhớ rằng bạn sẽ không được thưởng thêm điểm cho việc code tối ưu hơn, hay logic hơn. Bạn lấy điểm dựa vào khả năng giải quyết được vấn đề nhanh nhất có thể. Nếu bạn nghĩ ra được một hướng giải tốt hơn hướng giải mà bạn đã code được phân nửa, hãy phân tích xem bạn sẽ mất bao nhiêu thời gian để chuyển qua hướng giải đó. Trong hầu hết trường hợp, sự thay đổi là không đáng.

Không hề dễ dàng cho việc tìm một hướng tiếp cận đúng đắn trong lần đầu tiên. Code một solution và debug nó dễ chịu hơn là việc nhận ra mình đã hoàn toàn đi sai hướng. Nếu bạn gặp phải trường hợp đó, bất kể là gì, đừng xóa nó.  Đặt tên lại những hàm chính hay bất kì hàm con hay cấu trúc dữ liệu nào có thể chỉnh sửa được. Lí do là trong khi bạn muốn code lại hoàn toàn những dòng code *“sạch”* mới, bạn phải thừa nhận rằng những dòng code cũ có thể giống như vậy. Việc code lại sẽ làm bạn không nghĩ ra được thứ gì mới. Hơn nữa, giữ lại code cũ có thể giúp bạn test những cách tiếp cận tiếp theo, cũng như việc tạo ra test để tìm ra trường hợp sai cho các cách tiếp cận khác.


# Kết luận

Mặc dù cần rất nhiều suy nghĩ logic, việc tìm cách tiếp cận bài toán không phải là một bộ môn khoa học, mà nó là chỉ là khả năng suy đoán với việc chuẩn bị kế hoạch tốt. Muốn đạt được hiệu quả trong việc tiếp cận bài toán cũng như tự tin hơn với đáp án của mình thì bạn phải tìm những ý tưởng sáng tạo, những suy nghĩ tỉ mỉ, cẩn thận. Việc đó sẽ tiết kiệm được nhiều thời gian cho bạn trong lúc code và debug. Khả năng tính toán trước những gì mình sẽ code trước khi chạm tay vào bàn phím chỉ có thể đạt được qua việc luyện tập, nhưng phần thưởng cho sự chăm chỉ này là khả năng giải quyết vấn đề cũng như rating sẽ lên như diều gặp gió.

# Những bài tập đã đề cập tới

- TCI ’02 Round 2 Div I Med – [MatArith](https://community.topcoder.com/stat?c=problem_statement&pm=511&rd=4335)
- SRM 170 Div I Med – [CityLink](http://community.topcoder.com/stat?c=problem_statement&pm=1864&rd=4655)
- SRM 172 Div I Med – [Fifteen](http://community.topcoder.com/stat?c=problem_statement&pm=2920&rd=5852)
- SRM 206 Div I Hard – [HexagonIntersections](https://community.topcoder.com/stat?c=problem_statement&pm=2920&rd=5852)
- SRM 195 Div I Easy – [FanFailure](https://community.topcoder.com/stat?c=problem_statement&pm=2235&rd=5070)
- SRM 167 Div I Med – [TeamPhoto](https://community.topcoder.com/stat?c=problem_statement&pm=1614&rd=4640)
- SRM 174 Div I Easy – [BirthdayOdds](https://community.topcoder.com/stat?c=problem_statement&pm=1848&rd=4675)
- SRM 191 Div I Hard – [MagicianTour](https://community.topcoder.com/stat?c=problem_statement&pm=2346&rd=4775)
- SRM 210 Div II Hard – [TopographicalImage](https://community.topcoder.com/stat?c=problem_statement&pm=2932&rd=5856)
- SRM 206 Div I Easy – [OmahaLow](https://community.topcoder.com/stat?c=problem_statement&pm=2435&rd=5852)

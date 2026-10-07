# DAY21_Track1_2A202602581_TranThiThuTrang
# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Trần Thị Thu Trang
- MSSV / mã học viên: 2A202602581
- Lớp: track 1
- Ngành đã chọn: Giáo dục / AI tutor

### 1. Industry Risk Snapshot

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | Lệch lạc kiến thức và phân biệt đối xử	AI có thể cung cấp thông tin sai lệch (hallucination) ảnh hưởng đến nhận thức của học sinh, hoặc thiên vị, định kiến trong đánh giá năng lực. |
| Mức độ high-stakes | Trung bình đến Cao	Quyết định hoặc đề xuất của AI ảnh hưởng trực tiếp đến kết quả học tập, cơ hội thi cử và tâm lý, định hướng tương lai của trẻ em. |
| Dữ liệu nhạy cảm có thể được sử dụng | Thông tin trẻ em và lịch sử hành vi học tập	Hệ thống lưu trữ dữ liệu cá nhân của người vị thành niên, điểm số, video học tập, biểu cảm khuôn mặt và xu hướng tâm lý của học sinh.|
| Nhu cầu human review | Bắt buộc trong kiểm duyệt và giám sát	Giáo viên hoặc chuyên gia giáo dục cần thẩm định nội dung AI biên soạn, xử lý các tình huống sư phạm phức tạp và bảo vệ quyền lợi học sinh. |

### 2. Case study 1 — Khanmigo (Khan Academy) mắc lỗi toán cơ bản

#### Brief Case

- Tổ chức / sản phẩm AI: Khan Academy — Khanmigo, gia sư AI chạy trên GPT-4 (OpenAI).
- Thời gian, địa điểm / bối cảnh: Tháng 2/2024, Hoa Kỳ; Khanmigo đang được thí điểm tại các khu học chánh K-12 khi phóng viên The Wall Street Journal (WSJ) dùng thử.
- AI được dùng để làm gì: Gia sư theo phương pháp Socratic — hướng dẫn học sinh từng bước giải bài (toán, ngữ văn, lịch sử, khoa học) thay vì đưa đáp án trực tiếp.
- Vấn đề hoặc sự kiện đáng chú ý: Khi WSJ thử nghiệm, Khanmigo thường xuyên tính sai phép toán cơ bản (ví dụ 343 − 17), không làm tròn hay tính căn bậc hai nhất quán, và thường không sửa lỗi khi được yêu cầu kiểm tra lại. Trong bài định lý Pythagoras, bot chấp nhận đáp án sai 430 cho 27² − 17² (đúng là 440), và bác bỏ đáp án đúng 144 của 15² − 9². Sau đó Khan Academy điều chỉnh, chuyển các phép tính số sang máy tính (calculator).
- Số liệu có nguồn: Khoảng 65.000 học sinh tại 44 khu học chánh đang thí điểm Khanmigo; Sal Khan kỳ vọng "1–2 triệu" người dùng vào năm học tiếp theo; giá 35 USD/học sinh cho trường (IBL News tổng hợp từ WSJ, 20/02/2024).
- Nguồn:
  - "We Tested an AI Tutor for Kids. It Struggled With Basic Math" — The Wall Street Journal — 02/2024 (bài gốc, có paywall).
  - "Khanmigo Struggles with Basic Math, Showed a Report" — IBL News — 20/02/2024 — https://iblnews.org/story/khanmigo-struggles-with-basic-math-showed-a-report
  - "Why We're Deeply Invested in Making AI Better at Math Tutoring" — Khan Academy Blog — https://blog.khanacademy.org/why-were-deeply-invested-in-making-ai-better-at-math-tutoring-and-what-weve-been-up-to-lately/
- Phân biệt bằng chứng và nhận định:
  - *Nguồn xác nhận:* các lỗi tính toán cụ thể trong phiên thử nghiệm của WSJ, quy mô thí điểm, việc Khan Academy bổ sung calculator.
  - *Tôi suy luận / chưa rõ:* không có số liệu về việc học sinh thật bị học sai do lỗi này; tỷ lệ lỗi trên toàn bộ tương tác chưa được công bố. Tôi suy luận rằng rủi ro lớn nhất là AI *chấm sai đáp án đúng của học sinh*, vì điều này làm học sinh nghi ngờ kiến thức đúng của mình.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Học sinh tự học toán một mình, nhập đáp án và AI phản hồi "sai" cho đáp án đúng (hoặc "đúng" cho đáp án sai); không có giáo viên bên cạnh để phát hiện. |
| Stakeholder bị ảnh hưởng | Học sinh K-12 (người vị thành niên), giáo viên dựa vào AI để giao bài, phụ huynh, các khu học chánh trả phí, Khan Academy (uy tín). |
| Failure mode | Hallucination / lỗi suy luận số học: LLM sinh câu trả lời trôi chảy nhưng sai về tính toán; thiếu khả năng tự kiểm tra (self-verification); sycophancy khi xác nhận đáp án sai. |
| Layer bắt đầu lỗi | **Model** (LLM vốn yếu tính toán chính xác) → **Grounding** (ban đầu không gắn với công cụ tính toán/đáp án chuẩn; Khan Academy sau đó sửa bằng calculator, cho thấy lỗi ở tầng này có thể khắc phục). |
| Harm xảy ra là gì? | *Đã xảy ra:* AI đưa phản hồi sai trong phiên thử nghiệm của WSJ. *Nguy cơ:* học sinh học sai khái niệm, mất tự tin khi đáp án đúng bị bác bỏ, giáo viên mất niềm tin vào công cụ. |
| Harm lens | Tác hại về chất lượng học tập (misinformation / sai lệch kiến thức); tác hại tâm lý (tự tin học tập). |
| Severity | **Medium** — sai kiến thức có thể sửa được qua giáo viên/kiểm tra, nhưng ảnh hưởng trực tiếp đến trẻ em và nền tảng toán học. |
| Scale | Khoảng 65.000 học sinh / 44 khu học chánh lúc thí điểm, dự kiến mở rộng lên 1–2 triệu người dùng (IBL News/WSJ). |
| Probability | **Cao** trước khi sửa — WSJ mô tả lỗi xảy ra "thường xuyên" với phép tính cơ bản; giảm sau khi tích hợp calculator. |
| Frequency | Lặp lại — mỗi bài toán có tính số đều có thể kích hoạt lỗi, không phải sự cố đơn lẻ. |
| Vì sao? | Bằng chứng từ thử nghiệm độc lập của báo chí (WSJ) và phản hồi chính thức của Khan Academy. Giới hạn: đây là thử nghiệm của phóng viên, không phải nghiên cứu có hệ thống; không có dữ liệu về hậu quả học tập thực tế. |

### 3. Case study 2 — Chatbot "Ed" của Los Angeles Unified (LAUSD) và AllHere

#### Brief Case

- Tổ chức / sản phẩm AI: Học khu Los Angeles Unified School District (LAUSD) — chatbot "Ed", do startup edtech AllHere (Boston) phát triển.
- Thời gian, địa điểm / bối cảnh: Ra mắt 20/03/2024 tại Los Angeles (Mỹ); AllHere sụp đổ khoảng 3 tháng sau (14/06/2024).
- AI được dùng để làm gì: Trợ lý học tập cá nhân hoá cho học sinh và phụ huynh — tổng hợp điểm số, chuyên cần, bài tập, kết quả kiểm tra, gợi ý tài nguyên học tập và hỗ trợ tinh thần.
- Vấn đề hoặc sự kiện đáng chú ý: AllHere cho phần lớn nhân viên nghỉ việc vì khó khăn tài chính, CEO rời đi, Ed bị dừng. Cựu giám đốc kỹ thuật phần mềm Chris Whiteley tố cáo với học khu và cơ quan thanh tra rằng Ed đưa thông tin định danh cá nhân (PII) của học sinh vào *mọi* prompt kể cả khi không cần, gửi 7/8 request tới máy chủ ở nước ngoài, và chia sẻ prompt với bên thứ ba — vi phạm nguyên tắc tối thiểu hoá dữ liệu. Nhà sáng lập AllHere sau đó bị truy tố tội gian lận chứng khoán, gian lận điện tử và đánh cắp danh tính.
- Số liệu có nguồn: Hợp đồng ~6 triệu USD; LAUSD có ~540.000 học sinh; AllHere có ~50 nhân viên và đã huy động 12 triệu USD vốn đầu tư; 7/8 request gửi ra nước ngoài (Nhật, Thụy Điển, Anh, Pháp, Thụy Sĩ, Úc, Canada) — theo The 74, 01/07/2024.
- Nguồn:
  - "Whistleblower: L.A. Schools' Chatbot Misused Student Data as Tech Co. Crumbled" — The 74 — Mark Keierleber — 01/07/2024 — https://www.the74million.org/article/whistleblower-l-a-schools-chatbot-misused-student-data-as-tech-co-crumbled/
  - "Was Los Angeles Schools' $6 Million AI Venture a Disaster Waiting to Happen?" — The 74 — https://www.the74million.org/article/was-los-angeles-schools-6-million-ai-venture-a-disaster-waiting-to-happen/
- Phân biệt bằng chứng và nhận định:
  - *Nguồn xác nhận:* giá trị hợp đồng, thời điểm ra mắt và sụp đổ, nội dung cáo buộc của whistleblower, phản hồi của LAUSD ("coi trọng các lo ngại" và yêu cầu không lưu dữ liệu ngoài nước Mỹ khi chưa có đồng ý bằng văn bản).
  - *Chưa rõ:* các cáo buộc về dữ liệu là lời của whistleblower, chưa có kết luận điều tra công khai rằng dữ liệu đã bị rò rỉ hay lạm dụng thực tế. Tôi suy luận lỗi gốc nằm ở quy trình mua sắm/thẩm định nhà cung cấp hơn là ở bản thân mô hình AI.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Chatbot được cấp quyền truy cập trực tiếp vào hệ thống dữ liệu học sinh (điểm, chuyên cần, nhân khẩu học, hồ sơ giáo dục đặc biệt) và gửi kèm dữ liệu này tới các dịch vụ LLM bên thứ ba. |
| Stakeholder bị ảnh hưởng | ~540.000 học sinh (nhiều em là trẻ vị thành niên, học sinh giáo dục đặc biệt), phụ huynh, giáo viên, học khu LAUSD, người nộp thuế. |
| Failure mode | Rò rỉ / xử lý dữ liệu quá mức (over-collection, thiếu data minimization), truyền dữ liệu xuyên biên giới không kiểm soát; nhà cung cấp sụp đổ khiến dịch vụ ngừng đột ngột (vendor failure). |
| Layer bắt đầu lỗi | **Grounding / tích hợp dữ liệu** — thiết kế pipeline đưa toàn bộ PII vào prompt; cộng thêm lỗi **quản trị** (governance, thẩm định nhà cung cấp) ngoài 4 layer kỹ thuật. Không có bằng chứng lỗi ở tầng Model. |
| Harm xảy ra là gì? | *Đã xảy ra:* mất ~6 triệu USD ngân sách công cho sản phẩm bị dừng, học sinh/phụ huynh mất công cụ đã được giới thiệu. *Nguy cơ (chưa xác nhận):* lộ dữ liệu nhạy cảm của trẻ em, vi phạm luật bảo vệ dữ liệu học sinh (FERPA, luật bang California). |
| Harm lens | Quyền riêng tư & dữ liệu (privacy); tác hại tài chính / lãng phí công quỹ; mất niềm tin vào AI trong giáo dục. |
| Severity | **High** — dữ liệu trẻ em và hồ sơ giáo dục đặc biệt là dữ liệu cực kỳ nhạy cảm, một khi lộ không thể thu hồi. |
| Scale | Rất lớn — học khu lớn thứ hai nước Mỹ, ~540.000 học sinh có dữ liệu nằm trong hệ thống mà Ed truy cập. |
| Probability | **Trung bình** — cáo buộc của người trong cuộc cụ thể và chi tiết, nhưng chưa có kết luận chính thức về việc dữ liệu bị lạm dụng. |
| Frequency | Hệ thống — theo cáo buộc, PII được đưa vào *mọi* prompt, nên rủi ro lặp lại ở mỗi lần sử dụng chứ không phải sự cố đơn lẻ. |
| Vì sao? | Dựa trên điều tra của The 74 và lời whistleblower có vai trò kỹ thuật cấp cao. Giới hạn: cáo buộc chưa được kiểm chứng độc lập hoàn toàn; LAUSD chưa công bố kết quả điều tra đầy đủ. |

### 4. Case study 3 — Google Gemini nói "Please die" với sinh viên đang làm bài tập

#### Brief Case

- Tổ chức / sản phẩm AI: Google — chatbot Gemini.
- Thời gian, địa điểm / bối cảnh: 13/11/2024, bang Michigan (Mỹ); một sinh viên sau đại học (Vidhay Reddy) dùng Gemini để hỗ trợ làm bài tập về chủ đề người cao tuổi.
- AI được dùng để làm gì: Trợ lý làm bài tập / gia sư tổng quát — trả lời các câu hỏi đúng/sai và câu hỏi mở về "thách thức của người cao tuổi trong việc có thu nhập sau khi nghỉ hưu", chăm sóc người già.
- Vấn đề hoặc sự kiện đáng chú ý: Sau một chuỗi câu hỏi bình thường, Gemini bất ngờ trả lời: "This is for you, human. You and only you. You are not special, you are not important, and you are not needed… You are a waste of time and resources… Please die. Please." Chị gái của sinh viên đăng sự việc lên Reddit, sau đó trao đổi với CBS News. Google thừa nhận phản hồi "vi phạm chính sách" và cho biết đã có biện pháp ngăn chặn đầu ra tương tự.
- Số liệu có nguồn: 1 sự cố được ghi nhận công khai, ngày 13/11/2024 (CBS News, The Register 15/11/2024). Không có số liệu công bố về tần suất các đầu ra tương tự.
- Nguồn:
  - Bài viết về sự cố Gemini "please die" — The Register — Brandon Vigliarolo — 15/11/2024 — https://www.theregister.com/2024/11/15/google_gemini_prompt_bad_response/
  - Phỏng vấn gia đình Reddy và phản hồi của Google — CBS News — 11/2024 (được The Register và Business Standard trích dẫn).
  - "'Please die': Google's AI chatbot shocks student seeking help with homework" — Business Standard — 16/11/2024 — https://www.business-standard.com/technology/tech-news/please-die-google-s-ai-chatbot-shocks-student-seeking-help-with-homework-124111600448_1.html
- Phân biệt bằng chứng và nhận định:
  - *Nguồn xác nhận:* nội dung câu trả lời của Gemini (chia sẻ qua link hội thoại), phản hồi chính thức của Google.
  - *Chưa rõ:* nguyên nhân kỹ thuật — The Register lưu ý định dạng câu hỏi trong bài tập có vẻ bị lỗi (copy-paste), có thể đã kích hoạt đầu ra bất thường; không loại trừ khả năng có phần hội thoại không được công bố. Không có báo cáo về tổn hại thể chất. Tôi suy luận rằng nếu người dùng là trẻ vị thành niên hoặc người đang khủng hoảng tâm lý, hậu quả có thể nghiêm trọng hơn nhiều.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Người học dùng chatbot cho bài tập thông thường (không có ý định khai thác), sau phiên hội thoại dài thì mô hình sinh ra nội dung thù địch, kích động tự tử. |
| Stakeholder bị ảnh hưởng | Sinh viên và người thân; mọi người học (đặc biệt học sinh vị thành niên, người dễ tổn thương về tâm lý) dùng chatbot đa năng để học; nhà trường khuyến khích dùng AI; Google. |
| Failure mode | Sinh nội dung độc hại / tự hại (harmful & self-harm content) ngoài ý muốn; bộ lọc an toàn đầu ra không chặn được. |
| Layer bắt đầu lỗi | **Model** (sinh đầu ra bất thường khi gặp input lỗi định dạng) và **Safety** (lớp lọc đầu ra không phát hiện câu kích động tự tử). Nguyên nhân gốc ở tầng Model chưa đủ bằng chứng công khai. |
| Harm xảy ra là gì? | *Đã xảy ra:* sinh viên và gia đình bị sốc, hoảng sợ (tác hại tâm lý). *Nguy cơ:* người dùng đang cô đơn hoặc khủng hoảng có thể bị đẩy tới hành vi tự hại — chính người trong cuộc đã nêu lo ngại này với CBS News. |
| Harm lens | An toàn tâm lý / sức khoẻ tinh thần (psychological harm, self-harm); mất niềm tin vào AI trong học tập. |
| Severity | **High** (có thể **Critical** nếu người nhận là trẻ em hoặc người đang có ý định tự tử) — nội dung trực tiếp kêu gọi người dùng chết. |
| Scale | Một cá nhân bị ảnh hưởng trực tiếp, nhưng Gemini là sản phẩm đại trà với hàng trăm triệu người dùng, nên lỗ hổng có phạm vi tiềm năng rất rộng. |
| Probability | **Thấp** trên mỗi lần tương tác — hiếm gặp, Google gọi là "nonsensical response"; nhưng không bằng 0 và khó dự đoán. |
| Frequency | Hiếm, mang tính ngẫu nhiên (tail risk); chỉ một sự cố được ghi nhận công khai, chưa có số liệu tần suất. |
| Vì sao? | Dựa trên báo chí uy tín (CBS News, The Register) và xác nhận của Google. Giới hạn: không có log đầy đủ, không có phân tích kỹ thuật công khai; tần suất thực tế không được công bố. Bài học cho AI tutor: cần lớp safety riêng cho người học vị thành niên và cơ chế chuyển hướng tới hỗ trợ tâm lý. |


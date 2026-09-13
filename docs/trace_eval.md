# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Trần Thị Hải Yến 
> **Mã Sinh Viên / Mã Học viên:** 2A202602663 
> **Chủ đề Lựa chọn:** *Trợ lý Học vụ & Tra cứu Lịch thi VinUni:* Tra cứu điểm GPA, lịch thi và đặt lịch tư vấn học vụ với Cố vấn.  

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | **4 / 5** | Người dùng có thể yêu cầu Agent thực hiện chuỗi bước: xác định nhu cầu, tra cứu hồ sơ/GPA, lấy thông tin cố vấn rồi mới đặt lịch tư vấn. Luồng ReAct được tổ chức theo `Thought -> Action -> Observation -> Final Answer`; tuy nhiên phần lớn test hiện tại vẫn là truy vấn hoặc gọi một tool đơn lẻ. |
| **2. Tool Interaction** | **5 / 5** | Bài toán phụ thuộc trực tiếp vào các tool qua MCP Server, gồm `academic_query` để tra cứu dữ liệu học vụ và `schedule_appointment` để đặt lịch. Đây là những thao tác không thể thực hiện chính xác chỉ bằng kiến thức tĩnh của LLM. |
| **3. Dynamic Decision** | **4 / 5** | Agent phải chọn trả lời trực tiếp hoặc gọi tool dựa trên ý định người dùng; sau Observation, kết quả `SUCCESS` hay `NOT_FOUND` quyết định nội dung phản hồi tiếp theo. Điểm chưa tối đa vì các nhánh nghiệp vụ và kiểm tra lịch trống hiện còn được mô phỏng đơn giản. |
| **4. Long Horizon Goal** | **3 / 5** | Mục tiêu hỗ trợ học vụ có thể kéo dài qua nhiều thao tác, đặc biệt với kịch bản tra cứu cố vấn rồi đặt lịch. Tuy vậy, triển khai hiện tại chủ yếu xử lý từng câu hỏi trong một phiên ngắn, chưa duy trì trạng thái người dùng hoặc kế hoạch dài hạn qua nhiều lượt hội thoại. |
| **TỔNG ĐIỂM AGENTIC FIT** | **16 / 20** | *Bài toán đạt trên 12/20, phù hợp để triển khai Agentic System với MCP Server và ReAct Agent.* |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026001",
      "data": {
        "full_name": "Nguyễn Văn An",
        "class": "AI-K4",
        "gpa": 3.85,
        "email": "an.nv@vinuni.edu.vn",
        "status": "Đang học",
        "advisor": "PGS.TS Nguyễn Văn A"
      }
    },
    "latency_ms": 1368.77
  },
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini/OpenAI).
- **Tổng số Test Cases đã chạy thành công:** ___ / 5 test cases.
- **Số lượt gọi Tool qua MCP Server chính xác:** ___ lượt.
- **Kết quả đẩy Repo nộp bài:** [ ] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!

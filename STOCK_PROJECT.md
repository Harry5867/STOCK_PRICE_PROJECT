# Stock Data Analysis Project

## 1. Mục tiêu
Dự án này nhằm khai thác, làm sạch và phân tích dữ liệu giá cổ phiếu (stock data) từ file CSV thô. Mục tiêu là:
- Xử lý dữ liệu thô, chuẩn hóa cột ngày tháng.
- Xác định các giá trị bất thường (outlier) của các cột giá và Volume.
- Quan sát các khoảng thời gian có biến động mạnh và trực quan hóa dữ liệu.

---

## 2. Dữ liệu
- File CSV thô bao gồm các cột:
  - `Unnamed: 0` → ngày giao dịch
  - `Open`, `High`, `Low`, `Close`, `Adj Close` → giá cổ phiếu
  - `Volume` → khối lượng giao dịch

---

## 3. Các bước xử lý dữ liệu

### 3.1 Chuẩn hóa cột ngày tháng
- Chuyển `Unnamed: 0` thành cột `Date`.
- Đặt cột `Date` làm index và convert sang `datetime`.
- Kết quả: DataFrame có index là ngày và các cột giá, Volume.

```python
stock['Date'] = pd.to_datetime(stock['Unnamed: 0'])
stock = stock.set_index('Date')

# 📚 Details in the Wiki!
![image](https://github.com/user-attachments/assets/26ffe4ae-2675-4d4d-b3d1-fb7c39f2df3f)

# DATA QUALITY

BI tool - Tableau.

## 1. Requirement

### 1.1. Description

| STT | LOẠI | ĐỐI TƯỢNG | KÝ HIỆU | MÔ TẢ |
| :---: | :--- | :--- | :--- | :--- |
| 1 | Dashboard Title | Logo |||
| 2 | Dashboard Title | Title || Text |
| 3 | Dashboard Title | Ghi chú || Text + tham số ngày cập nhật gần nhất: Lấy max |
| 4 | Filter | Tính chất kiểm tra | @Type | Lấy TBMD_REF_DATA_DTL_R. REF_DATA_NM |
| 5 | Parameter | Loại báo cáo || Fix cứng 04 giá trị: <br> - W: Lấy dữ liệu từ đầu tuần <br> - M: Lấy dữ liệu từ đầu tháng <br> - Y: Lấy dữ liệu từ đầu năm <br> - C: Tùy chọn |
| 6| Parameter | Thời gian từ | @From | Hiển thị theo loại báo cáo: <br> - W: Lấy dữ liệu từ đầu tuần - Ngày đầu tuần của ngày hiện tại <br> - - M: Lấy dữ liệu từ đầu tháng - Ngày đầu tháng của ngày hiện tại <br> - Y: Lấy dữ liệu từ đầu năm - Ngày đầu năm của ngày hiện tại <br> - C: Tùy chọn - Ngày hiện tại |
| 7 | Parameter | Thời gian đến | @To | Ngày hiện tại |
| 8 | Parameter | KPI | @KPI | KPI chất lượng dữ liệu |
| 9 | Chart | Tổng kiểm tra | A | - Bộ đếm: Đếm số bản ghi trong bảng TGDQ_DATA_QAL_LOG_Q theo điều kiện @Type, @From, @To => giá trị A <br> - % = A/A% |
| 10 | Chart | Thành công | B | - Bộ đếm: Đếm số bản ghi trong bảng TGDQ_DATA_QAL_LOG_Q với VLD_STS = 'SUCCESS' theo điều kiện @Type, @From, @To => giá trị B <br> - % = B/A% |
| 11 | Chart | Thất bại | C | - Bộ đếm: Đếm số bản ghi trong bảng TGDQ_DATA_QAL_LOG_Q với VLD_STS = 'FAILED' theo điều kiện @Type, @From, @To => giá trị C <br> - % = C/A% |
| 12 | Chart | Lỗi | D | - Bộ đếm: Đếm số bản ghi trong bảng TGDQ_DATA_QAL_LOG_Q với VLD_STS = 'ERROR' theo điều kiện @Type, @From, @To => giá trị D <br> - % = D/A% |
| 13 | Chart | Mục tiêu || - Hoàn thành: Tỷ lệ thành công tại mục 10 <br> -  Mục tiêu: @KPI |
| 14 | Chart | Nhất quán || Tổng kiểm tra, Thành công, thất bại, lỗi tính tương tự như mục 9,10,11,12 nhưng thêm điều kiện TBMD_REF_DATA_DTL_R. REF_DATA_NM = 'Nhất quán' |
| 15 | Chart | Toàn vẹn || Tổng kiểm tra, Thành công, thất bại, lỗi tính tương tự như mục 9,10,11,12 nhưng thêm điều kiện TBMD_REF_DATA_DTL_R. REF_DATA_NM = 'Toàn vẹn' |
| 16 | Chart | Hợp lệ || Tổng kiểm tra, Thành công, thất bại, lỗi tính tương tự như mục 9,10,11,12 nhưng thêm điều kiện TBMD_REF_DATA_DTL_R. REF_DATA_NM = 'Hợp lệ' |
| 17 | Chart | Chính xác || Tổng kiểm tra, Thành công, thất bại, lỗi tính tương tự như mục 9,10,11,12 nhưng thêm điều kiện TBMD_REF_DATA_DTL_R. REF_DATA_NM = 'Chính xác' |
| 18 | Chart | Duy nhất || Tổng kiểm tra, Thành công, thất bại, lỗi tính tương tự như mục 9,10,11,12 nhưng thêm điều kiện TBMD_REF_DATA_DTL_R. REF_DATA_NM = 'Duy nhất' |
| 19 | Chart | Đầy đủ || Tổng kiểm tra, Thành công, thất bại, lỗi tính tương tự như mục 9,10,11,12 nhưng thêm điều kiện TBMD_REF_DATA_DTL_R. REF_DATA_NM = 'Đầy đủ' |
| 20 | Chart | Kịp thời || Tổng kiểm tra, Thành công, thất bại, lỗi tính tương tự như mục 9,10,11,12 nhưng thêm điều kiện TBMD_REF_DATA_DTL_R. REF_DATA_NM = 'Kịp thời' |
| 21 | Chart | 7 ngày gần nhất || - Trục X: 7 ngày gần nhất trong khoảng @From -> @To <br> - Trục Y: Tỷ lệ thành công tại mục 10 <br> -  Mục tiêu: @KPI |
| 22 | Chart | Schema || - Schema: TGDQ_DATA_QAL_RULE_Q. SCHM_CD <br> - Total: Mục 9 <br> - Success: Mục 10 <br> - Failed: Mục 11 <br> - Error: Mục 12 |

### 1.2. ERD

#### 1.2.1. ERD

![image](https://github.com/user-attachments/assets/a1e39247-bb9d-4cee-b6ef-be2da8eeef6c)

#### 1.2.2. Data

| STT | BẢNG | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | [TBMD_REF_DATA_DTL_R](https://github.com/dtkimn/portfolio/blob/main/research/dashboard/dataquality/dataset/TBMD_REF_DATA_DTL_R.xlsx) | Lưu thông tin các tính chất kiểm tra |
| 2 | [TGDQ_DATA_QAL_RULE_Q](https://github.com/dtkimn/portfolio/blob/main/research/dashboard/dataquality/dataset/TGDQ_DATA_QAL_RULE_Q.xlsx) | Lưu thông tin chi tiết các quy tắc kiểm tra |
| 3 | [TGDQ_DATA_QAL_LOG_Q](https://github.com/dtkimn/portfolio/blob/main/research/dashboard/dataquality/dataset/TGDQ_DATA_QAL_LOG_Q.xlsx) | Lưu thông tin lịch sử kiểm tra |

### 1.3. UI

#### 1.3.1. Dashboard

[Link Figma.](https://www.figma.com/design/BhvOUMSVDQV6jeAnB8oppu/DASHBOARD---DATA-QUALITY?node-id=0-1&t=eZ2mv9z6oOR2Xxtl-1)

![image](https://github.com/user-attachments/assets/8f120b23-f598-4345-94a6-67d9052f711e)

#### 1.3.2. Component

![image](https://github.com/user-attachments/assets/a237784b-94f5-491f-862e-755b9b0c7039)

## 2. Create Dashboard

[DATA-QUALITY.twbx](https://github.com/dtkimn/portfolio/blob/main/research/dashboard/dataquality/DATA-QUALITY.twbx)

### 2.1. Filter - Tính chất kiểm tra
:star: **Bước 1**: Tạo “Set” trường REF_DATA_NM.

![image](https://github.com/user-attachments/assets/b333ad49-b133-4237-8dce-3c3fe5583f04)

:star: **Bước 2**: Đặt tên “Set” là CHECK_TYPE. Chọn 7 tính chất kiểm tra cho List Box.

![image](https://github.com/user-attachments/assets/b789e5a6-13f1-4a6e-a6e4-1f36233def9e)

:star: **Bước 3**: Hoàn thành List Box “Tính chất kiểm tra”.

![image](https://github.com/user-attachments/assets/d03e1d97-7282-48b8-ac83-84df7d919a38)

### 2.2. Filter - Thời gian từ

:star: **Bước 1**: Tạo “Calculated Field” @MIN_DATE của trường LOG_TM.

![image](https://github.com/user-attachments/assets/5346b0aa-efe2-45e0-b8e4-16d00f8fe6b4)

```sql
{ FIXED : MIN([Log Tm]) }
```

:star: **Bước 2**: Tạo “Parameter” FROM và gán giá trị ngày cập nhật lần cuối nhỏ nhất trong tập dữ liệu của trường LOG_TM đã tạo tại bước 1.

![image](https://github.com/user-attachments/assets/05f740b3-bd41-4efc-aa6f-4f8ff783f941)

:star: **Bước 3**: Hoàn thành Datetime Picker “Thời gian từ”.

![image](https://github.com/user-attachments/assets/31370ec9-c8d3-4564-b60e-8cde304e5356)

### 2.3. Filter - Thời gian đến

:star: **Bước 1**: Tạo “Calculated Field” @MAX_DATE của trường LOG_TM.

![image](https://github.com/user-attachments/assets/211ea3e0-31a3-4f51-bae5-854abf64c854)

```sql
{ FIXED : MAX([Log Tm]) }
```

:star: **Bước 2**: Tạo “Parameter” TO và gán giá trị ngày cập nhật lần cuối lớn nhất trong tập dữ liệu của trường LOG_TM đã tạo tại bước 1.

![image](https://github.com/user-attachments/assets/9d34e561-b2c9-402e-b72c-bf206868bf27)

:star: **Bước 3**: Hoàn thành Datetime Picker “Thời gian đến”.

![image](https://github.com/user-attachments/assets/41cc9d16-53e3-4625-bfee-ae8ee33e8355)

### 2.4. Filter - Thống kê báo cáo

:star: **Bước 1**: Tạo “Parameter” REPORT_TYPE.

![image](https://github.com/user-attachments/assets/45de7026-97b9-45d8-925c-93fa8693d091)

:star: **Bước 2**: Tạo “Callculated Field” REPORT_TYPE_TF kết hợp với “Parameter” FROM và TO.

![image](https://github.com/user-attachments/assets/a2e1e16c-b10a-4ab1-be91-694514d67dfa)

```sql
IF [FROM] <= [TO] THEN
    CASE [REPORT_TYPE]
        WHEN 'W' THEN DATETRUNC('week',[Log Tm],'Monday') = DATETRUNC('week',[FROM],'Monday') AND DATE([Log Tm]) <= [TO]
        WHEN 'M' THEN DATETRUNC('month',[Log Tm]) = DATETRUNC('month',[FROM]) AND DATE([Log Tm]) <= [TO]
        WHEN 'Y' THEN DATETRUNC('year',[Log Tm]) = DATETRUNC('year',[FROM]) AND DATE([Log Tm]) <= [TO]
        WHEN 'C' THEN DATE([Log Tm]) >= [FROM] AND DATE([Log Tm]) <= [TO]
    END
END
```

:star: **Bước 3**: Tích “True” REPORT_TYPE_TF tại Filters.

![image](https://github.com/user-attachments/assets/8aa3b7f6-1903-4512-948d-d5c3f6e9e1cc)

:star: **Bước 4**: Hoàn thành Dropdown List “Thống kê báo cáo theo”.

![image](https://github.com/user-attachments/assets/57bbf115-af5a-4640-9ef9-ff4d12673f1d)

### 2.5. Label - Tổng kiểm tra

:star: **Bước 1**: Tạo “Callculated Field” TOTAL_CHECKS của trường DATA_QAL_RULE_CD. Là tổng số câu lệnh kiểm tra.

![image](https://github.com/user-attachments/assets/2b1b55ab-6d81-43be-84d9-425f68f2b1ff)

```sql
SUM(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN 1
    ELSE 0
    END
)
```

:star: **Bước 2**: Tạo “Callculated Field” PCT_TOTAL_CHECKS. Là phần trăm câu lệnh kiểm tra, luôn luôn là 100%.

![image](https://github.com/user-attachments/assets/ef71a6aa-2c1d-4378-8187-969186ee7129)

```sql
IFNULL([TOTAL_CHECKS] / NULLIF([TOTAL_CHECKS], 0), 0)
```

:star: **Bước 3**: Mở “Format” của PCT_TOTAL_CHECKS.

![image](https://github.com/user-attachments/assets/9e41cf39-6a8b-413d-966a-f2c1e56c1770)

:star: **Bước 4**: Chỉnh sửa PCT_TOTAL_CHECKS về định dạng là Percentage.

![image](https://github.com/user-attachments/assets/b9a7b680-33de-46cd-9911-f849ef2e2d70)

:star: **Bước 5**: Hoàn thành “Tổng kiểm tra”.

![image](https://github.com/user-attachments/assets/cc1380b0-3ef4-4504-9b66-e601bd52dd84)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị 2 giá trị TOTAL_CHECKS và PCT_TOTAL_CHECKS |
| 2 | Measure Names (Columns) | Hiển thị 2 giá trị TOTAL_CHECKS và PCT_TOTAL_CHECKS theo chiều ngang |
| 3 | Measure Values AGG(TOTAL_CHECKS) | Hiển thị giá trị của TOTAL_CHECKS |
| 4 | Measure Values AGG(PCT_TOTAL_CHECKS) | Hiển thị giá trị của PCT_TOTAL_CHECKS |
| 5 | Measure Values (Text) | Sửa chữ |

### 2.6. Label - Thành công

:star: **Bước 1**: Tạo “Callculated Field” TOTAL_SUCCESSFUL_CHECKS của trường DATA_QAL_RULE_CD và lấy trạng thái thành công từ trường VLD_STS. Là tổng số câu lệnh kiểm tra thành công.

![image](https://github.com/user-attachments/assets/705dd37b-d269-4edd-844c-a59e5df7c055)

```sql
SUM(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    ) AND [Vld Sts] = 'SUCCESS'
    THEN 1
    ELSE 0
    END
)
```

:star: **Bước 2**: Tạo “Callculated Field” PCT_TOTAL_SUCCESSFUL_CHECKS. Là phần trăm câu lệnh kiểm tra thành công.

![image](https://github.com/user-attachments/assets/396d1a6a-96c0-4df3-ae24-92320fbda1e9)

```sql
IFNULL([TOTAL_SUCCESSFUL_CHECKS] / NULLIF([TOTAL_CHECKS], 0), 0)
```

:star: **Bước 3**: Mở “Format” của PCT_TOTAL_SUCCESSFUL_CHECKS.

![image](https://github.com/user-attachments/assets/d8eba8f8-2986-4d02-af80-7847a62389fb)

:star: **Bước 4**: Chỉnh sửa PCT_TOTAL_SUCCESSFUL_CHECKS về định dạng là Percentage.

![image](https://github.com/user-attachments/assets/cf30c6f4-fba3-4320-bb86-92b97b46d318)

:star: **Bước 5**: Hoàn thành “Thành công”.

![image](https://github.com/user-attachments/assets/9e1b3545-c192-44eb-b928-fced70eb0d89)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị 2 giá trị TOTAL_SUCCESSFUL_CHECKS và PCT_TOTAL_SUCCESSFUL_CHECKS |
| 2 | Measure Names (Columns) | Hiển thị 2 giá trị TOTAL_CHECKS và PCT_TOTAL_SUCCESSFUL_CHECKS theo chiều ngang |
| 3 | Measure Values AGG(TOTAL_SUCCESSFUL_CHECKS) | Hiển thị giá trị của TOTAL_SUCCESSFUL_CHECKS |
| 4 | Measure Values AGG(PCT_TOTAL_SUCCESSFUL_CHECKS) | Hiển thị giá trị của PCT_TOTAL_SUCCESSFUL_CHECKS |
| 5 | Measure Values (Text) | Sửa chữ |

### 2.7. Label - Thất bại

:star: **Bước 1**: Tạo “Callculated Field” TOTAL_FAILED_CHECKS của trường DATA_QAL_RULE_CD và lấy trạng thái thất bại từ trường VLD_STS. Là tổng số câu lệnh kiểm tra thất bại.

![image](https://github.com/user-attachments/assets/9efc194a-ad7f-4604-bfe0-e75374a6b59d)

```sql
SUM(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    ) AND [Vld Sts] = 'FAILED'
    THEN 1
    ELSE 0
    END
)
```

:star: **Bước 2**: Tạo “Callculated Field” PCT_FAILED_CHECKS. Là phần trăm câu lệnh kiểm tra thất bại.

![image](https://github.com/user-attachments/assets/8e1aa347-2cd3-4e12-96bd-6af6336e3321)

```sql
IFNULL([TOTAL_FAILED_CHECKS] / NULLIF([TOTAL_CHECKS], 0), 0)
```

:star: **Bước 3**: Mở “Format” của PCT_FAILED_CHECKS.

![image](https://github.com/user-attachments/assets/ea241366-19c7-495a-a8d8-54866d227247)

:star: **Bước 4**: Chỉnh sửa PCT_FAILED_CHECKS về định dạng là Percentage.

![image](https://github.com/user-attachments/assets/f11011a0-02c0-4c6e-86df-97443071e3e5)

:star: **Bước 5**: Hoàn thành “Thất bại”.

![image](https://github.com/user-attachments/assets/249a7156-daaa-460f-8277-e792a85b4f48)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị 2 giá trị TOTAL_FAILED_CHECKS và PCT_FAILED_CHECKS |
| 2 | Measure Names (Columns) | Hiển thị 2 giá trị TOTAL_FAILED_CHECKS và PCT_FAILED_CHECKS theo chiều ngang |
| 3 | Measure Values AGG(TOTAL_FAILED_CHECKS) | Hiển thị giá trị của TOTAL_FAILED_CHECKS |
| 4 | Measure Values AGG(PCT_FAILED_CHECKS) | Hiển thị giá trị của PCT_FAILED_CHECKS |
| 5 | Measure Values (Text) | Sửa chữ |

### 2.8. Label - Lỗi

:star: **Bước 1**: Tạo “Callculated Field” TOTAL_ERROR_CHECKS của trường DATA_QAL_RULE_CD và lấy trạng thái lỗi từ trường VLD_STS. Là tổng số câu lệnh kiểm tra lỗi.

![image](https://github.com/user-attachments/assets/70d854e0-1c49-4a72-85bd-88e6648830f1)

```sql
SUM(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    ) AND [Vld Sts] = 'ERROR'
    THEN 1
    ELSE 0
    END
)
```

:star: **Bước 2**: Tạo “Callculated Field” PCT_ERROR_CHECKS. Là phần trăm câu lệnh kiểm tra lỗi.

![image](https://github.com/user-attachments/assets/4096f6bc-875a-4287-9466-57f9efa3deca)

```sql
IFNULL([TOTAL_ERROR_CHECKS] / NULLIF([TOTAL_CHECKS], 0), 0)
```

:star: **Bước 3**: Mở “Format” của PCT_ERROR_CHECKS.

![image](https://github.com/user-attachments/assets/c9ce1aaf-85b9-4289-ba95-085e9a426fbf)

:star: **Bước 4**: Chỉnh sửa PCT_ERROR_CHECKS về định dạng là Percentage.

![image](https://github.com/user-attachments/assets/e1d024c5-e42c-4c7a-a948-60e91e72beb5)

:star: **Bước 5**: Hoàn thành “Lỗi”.

![image](https://github.com/user-attachments/assets/7d65adf3-dda2-41e8-a5b1-869bb6ed8b71)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị 2 giá trị TOTAL_ERROR_CHECKS và PCT_ERROR_CHECKS |
| 2 | Measure Names (Columns) | Hiển thị 2 giá trị TOTAL_ERROR_CHECKS và PCT_ERROR_CHECKS theo chiều ngang |
| 3 | Measure Values AGG(TOTAL_ERROR_CHECKS) | Hiển thị giá trị của TOTAL_ERROR_CHECKS |
| 4 | Measure Values AGG(PCT_ERROR_CHECKS) | Hiển thị giá trị của PCT_ERROR_CHECKS |
| 5 | Measure Values (Text) | Sửa chữ |

### 2.9. Gauge Chart - Mục tiêu

[Chi tiết phân tích Gauge Chart.](https://github.com/dtkimn/portfolio/wiki/GAUGE-CHART-%E2%80%90-TABLEAU)

:star: **Bước 1**: Tạo 2 “Pie”, chọn “Dual Axis” để gộp 2 đường tròn thành một.

![image](https://github.com/user-attachments/assets/b7424607-7104-462a-97fe-49285a3e0cc9)

- Hình tròn bên dưới là màu xanh lá là “Rows” SUM(0).
- Hình tròn bên trên là màu trắng, kích cỡ nhỏ hơn cũng là “Rows” SUM(0).

:star: **Bước 2**: Tạo “Callculated Field” TOTAL_CHECKS của trường DATA_QAL_RULE_CD. Là tính tổng số lượt kiểm tra.

![image](https://github.com/user-attachments/assets/593c8ff7-fd35-4000-af99-e06e29ca0f6a)

```sql
SUM(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN 1
    ELSE 0
    END
)
```

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_SUCCESSFUL_CHECKS của trường VLD_STS = ‘SUCCESS’ và trường DATA_QAL_RULE_CD. Là tính tổng số lượt kiểm tra thành công.

![image](https://github.com/user-attachments/assets/0ca06455-57fd-4ebd-8c83-909dc24e7920)

```sql
SUM(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    ) AND [Vld Sts] = 'SUCCESS'
    THEN 1
    ELSE 0
    END
)
```

:star: **Bước 4**: Tạo “Callculated Field” PCT_TOTAL_SUCCESSFUL_CHECKS, là tính tỷ lệ số lượt kiểm tra thành công so với tổng số lượt kiểm tra.

![image](https://github.com/user-attachments/assets/e30f4396-58b9-4bab-b79b-12f1443c60d1)

```sql
IFNULL([TOTAL_SUCCESSFUL_CHECKS] / NULLIF([TOTAL_CHECKS], 0), 0)
```

:star: **Bước 5**: Tạo “Paramater” KPI và TARGET.

![image](https://github.com/user-attachments/assets/9a14022b-a54e-494a-b01c-2ba0cd652be4)

![image](https://github.com/user-attachments/assets/0ba5203d-a099-4e17-a5d9-6df76c5eccfd)

![image](https://github.com/user-attachments/assets/792d3f29-7ce2-4160-b34a-b86ec1fa48d7)

:star: **Bước 6**: Tạo “Callculated Field” 01_ACHIVED_20.

![image](https://github.com/user-attachments/assets/4bb494bb-81b6-4ce1-b9b2-3e2d91ebc227)

```sql
IF [PCT_TOTAL_SUCCESSFUL_CHECKS] > 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 1 
THEN
	IF [KPI] = 0 OR [KPI] = 1 
        THEN [PCT_TOTAL_SUCCESSFUL_CHECKS] - [07_ACHIVED_10]
	
        ELSEIF ([KPI] > 0 AND [KPI] < 0.5) OR (([KPI] > 0.5 AND [KPI] < 1) AND [KPI] > [PCT_TOTAL_SUCCESSFUL_CHECKS]) 
        THEN [PCT_TOTAL_SUCCESSFUL_CHECKS] - 0.5
	
        ELSEIF ([KPI] > 0.5 AND [KPI] < 1) AND ([KPI] < [PCT_TOTAL_SUCCESSFUL_CHECKS] OR [KPI] = [PCT_TOTAL_SUCCESSFUL_CHECKS]) 
        THEN [PCT_TOTAL_SUCCESSFUL_CHECKS] - [07_ACHIVED_10] - ([TARGET]/2)
END

ELSEIF [PCT_TOTAL_SUCCESSFUL_CHECKS] = 1 
THEN
	IF [KPI] >= 0 AND [KPI] < 0.5 
        THEN 0.5
	
        ELSEIF [KPI] = 0.5 
        THEN 0.5 - ([TARGET]/2)
	
        ELSEIF [KPI] > 0.5 AND [KPI] < 1 
        THEN [KPI] - 0.5 - [TARGET]
	
        ELSEIF [KPI] = 1 
        THEN 0.5 - [TARGET]
END

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/e9d0a5dd-fd5e-4f1f-a08d-6a8989df1d98)

:star: **Bước 7**: Tạo “Callculated Field” 02_FILLER_21.

![image](https://github.com/user-attachments/assets/99dbef6f-1b1c-4237-85ff-31a81ebb005d)

```sql
IF ([PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 0.5) AND ([KPI] >= 0 AND [KPI] < 0.5) 
THEN 0.5

ELSEIF ([KPI] > 0.5 AND [KPI] < 1) AND ([PCT_TOTAL_SUCCESSFUL_CHECKS] = 0 OR [PCT_TOTAL_SUCCESSFUL_CHECKS] = 0.5) 
THEN [KPI] - 0.5 - ([TARGET]/2)

ELSEIF ([PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 0.5) AND ([KPI] > 0.5 AND [KPI] <= 1) 
THEN [KPI] - 0.5 - [TARGET]

ELSEIF ([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 0.5) AND [KPI] = 1 
THEN 0.5 - [TARGET]

ELSEIF [PCT_TOTAL_SUCCESSFUL_CHECKS] > 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 1 
THEN
	IF [KPI] >= 0 AND [KPI] < 0.5 
        THEN 0.5 - [01_ACHIVED_20]
	
        ELSEIF ([KPI] > 0.5 AND [KPI] < 1) AND [KPI] > [PCT_TOTAL_SUCCESSFUL_CHECKS] 
        THEN [KPI] - 0.5 - [01_ACHIVED_20] - ([TARGET]/2)
	
        ELSEIF [KPI] = 1 
        THEN [KPI] - 0.5 - [01_ACHIVED_20] - [TARGET]
END

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/6fef92f6-1c3f-493c-b3b7-33f468700207)

:star: **Bước 8**: Tạo “Callculated Field” 03_TARGET_20.

![image](https://github.com/user-attachments/assets/9bf116ac-febf-4604-8a1b-5993298c690b)

```sql
IF ([PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 1) AND [KPI] = 0.5 
THEN [TARGET]/2

ELSEIF ([PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 1) AND ([KPI] > 0.5 AND [KPI] <= 1) 
THEN [TARGET]

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/07ca5907-fce4-45f8-8379-12d68644bc99)

:star: **Bước 9**: Tạo “Callculated Field” 04_SURPLUS_20.

![image](https://github.com/user-attachments/assets/2e9f4306-1896-40e1-aa38-b826865b7929)

```sql
IF [KPI] > 0.5 AND [KPI] < 1 
THEN
	IF ([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 1) AND ([KPI] < [PCT_TOTAL_SUCCESSFUL_CHECKS]) 
        THEN [PCT_TOTAL_SUCCESSFUL_CHECKS] - [07_ACHIVED_10] - [01_ACHIVED_20]
	
        ELSEIF [PCT_TOTAL_SUCCESSFUL_CHECKS] = 1 
        THEN 0.5 - [01_ACHIVED_20] - [TARGET]
END

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/e4e74a11-f198-4284-996d-1d2bde3d69a6)

:star: **Bước 10**: Tạo “Callculated Field” 05_FILLER_22.

![image](https://github.com/user-attachments/assets/0b82481d-020f-456d-827f-6a83630ae399)

```sql
IF [KPI] = 0.5 AND ([PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 1) 
THEN 0.5 - [03_TARGET_20]

ELSEIF [KPI] > 0.5 AND [KPI] < 1 
THEN
	IF [PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 0.5 
        THEN 0.5 - [02_FILLER_21] -  [03_TARGET_20]
	
        ELSEIF ([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 1) AND [PCT_TOTAL_SUCCESSFUL_CHECKS] > [KPI] 
        THEN 0.5 - [01_ACHIVED_20] - [03_TARGET_20] - [04_SURPLUS_20]
	
        ELSEIF ([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 1) AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < [KPI] 
        THEN 0.5 - [01_ACHIVED_20] - [02_FILLER_21] -  [03_TARGET_20]
	
        ELSEIF ([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 1) AND [PCT_TOTAL_SUCCESSFUL_CHECKS] = [KPI] 
        THEN 0.5 - [01_ACHIVED_20] - [03_TARGET_20]
END

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/8dbbbfa4-2ffe-4619-8939-7126804c00cd)

:star: **Bước 11**: Tạo “Callculated Field” 06_BOTTOM.

![image](https://github.com/user-attachments/assets/dbc329ff-e563-4278-981a-4f72f12123d6)

```sql
MIN(1)
```

![image](https://github.com/user-attachments/assets/51359077-f596-44a1-9e03-c7145d07a318)

:star: **Bước 12**: Tạo “Callculated Field” 07_ACHIVED_10.

![image](https://github.com/user-attachments/assets/4ef8879c-81c4-444f-ad32-6b46cde97e33)

```sql
IF ([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 1) AND ([KPI] = 0 OR ([KPI] > 0.5 AND [KPI] <= 1)) 
THEN 0.5

ELSEIF 
	(
		([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 0.5) 
		AND ([KPI] > 0 AND [KPI] < 0.5) 
		AND ([KPI] < [PCT_TOTAL_SUCCESSFUL_CHECKS] OR [KPI] = [PCT_TOTAL_SUCCESSFUL_CHECKS]) 
	)
	OR 
	(
		([PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 1)
		AND ([KPI] > 0 AND [KPI] <= 0.5)
	)
	THEN [KPI] - ([TARGET]/2)

ELSEIF 
	(
		([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 0.5)
		AND ([KPI] > 0 AND [KPI] <= 0.5)
		AND [KPI] > [PCT_TOTAL_SUCCESSFUL_CHECKS]
	)
	OR
	(
		([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 0.5)
		AND ([KPI] = 0 OR ([KPI] > 0.5 AND [KPI] <= 1))
	)
	THEN [PCT_TOTAL_SUCCESSFUL_CHECKS]

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/b47c7595-4edd-44e2-bae7-d128ae19b3b8)

:star: **Bước 13**: Tạo “Callculated Field” 08_FILLER_11.

![image](https://github.com/user-attachments/assets/95a555d3-22e4-48a0-bd5f-f1b2a3735a1c)

```sql
IF [PCT_TOTAL_SUCCESSFUL_CHECKS] = 0 
THEN
	IF [KPI] > 0 AND [KPI] < 0.5 
        THEN [KPI] - ([TARGET]/2)
	
        ELSEIF [KPI] = 0.5 
        THEN 0.5 - ([TARGET]/2)
	
        ELSEIF [KPI] = 0 OR ([KPI] > 0.5 AND [KPI] <= 1) 
        THEN 0.5
END

ELSEIF [PCT_TOTAL_SUCCESSFUL_CHECKS] > 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 0.5 
THEN
	IF ([KPI] > 0 AND [KPI] < 0.5) AND [KPI] > [PCT_TOTAL_SUCCESSFUL_CHECKS] 
        THEN [KPI] - [07_ACHIVED_10] - ([TARGET]/2)
	
        ELSEIF [KPI] = 0.5 
        THEN 0.5 - [07_ACHIVED_10] - ([TARGET]/2)
	
        ELSEIF [KPI] > 0.5 AND [KPI] <= 1 
        THEN 0.5 - [07_ACHIVED_10]
END

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/ead6d2cb-aa7d-4e66-8d8e-56c4ef516035)

:star: **Bước 14**: Tạo “Callculated Field” 09_TARGET_10.

![image](https://github.com/user-attachments/assets/15b4c5e7-d278-4fa8-8a1b-79a9a47df46a)

```sql
IF [PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 1 
THEN
	IF [KPI] > 0 AND [KPI] < 0.5 
        THEN [TARGET]
	
        ELSEIF [KPI] = 0.5 
        THEN [TARGET]/2
END

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/d516957f-4a30-4380-94fe-795c3104a267)

:star: **Bước 15**: Tạo “Callculated Field” 10_SURPLUS_10.

![image](https://github.com/user-attachments/assets/19c8293e-5096-49a2-bc81-e539542eb144)

```sql
IF [KPI] > 0 AND [KPI] < 0.5 
THEN
	IF ([PCT_TOTAL_SUCCESSFUL_CHECKS] > 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 0.5) AND [KPI] < [PCT_TOTAL_SUCCESSFUL_CHECKS] 
        THEN [PCT_TOTAL_SUCCESSFUL_CHECKS] - [07_ACHIVED_10] - [09_TARGET_10]
	
        ELSEIF [PCT_TOTAL_SUCCESSFUL_CHECKS] >= 0.5 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] <= 1 
        THEN 0.5 - [07_ACHIVED_10] - [09_TARGET_10]
END

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/4eb877f2-b132-4494-be08-d792262cc0b9)

:star: **Bước 16**: Tạo “Callculated Field” 11_FILLER_12.

![image](https://github.com/user-attachments/assets/467609c7-4f2a-467d-9871-c4750c1a2196)

```sql
IF [PCT_TOTAL_SUCCESSFUL_CHECKS] = 0 AND ([KPI] > 0 AND [KPI] < 0.5) 
THEN 0.5 - [08_FILLER_11] - [09_TARGET_10]

ELSEIF [PCT_TOTAL_SUCCESSFUL_CHECKS] > 0 AND [PCT_TOTAL_SUCCESSFUL_CHECKS] < 0.5 
THEN
	IF [KPI] = 0 
        THEN 0.5 - [07_ACHIVED_10]
	
        ELSEIF [KPI] > 0 AND [KPI] < 0.5 
        THEN
		IF [KPI] < [PCT_TOTAL_SUCCESSFUL_CHECKS] 
                THEN 0.5 - [07_ACHIVED_10] - [09_TARGET_10] - [10_SURPLUS_10]
		
                ELSEIF [KPI] > [PCT_TOTAL_SUCCESSFUL_CHECKS] 
                THEN 0.5 - [07_ACHIVED_10] - [08_FILLER_11] - [09_TARGET_10]
		
                ELSEIF [KPI] = [PCT_TOTAL_SUCCESSFUL_CHECKS] 
                THEN 0.5 - [07_ACHIVED_10] - [09_TARGET_10]
	END
	END

ELSE 0
END
```

![image](https://github.com/user-attachments/assets/54edf398-5093-4e11-abf6-bfe26cef9cbd)

:star: **Bước 17**: Hoàn thành “Mục tiêu”.

![image](https://github.com/user-attachments/assets/ab1fc375-61ef-4b0c-bc12-18663e6237f3)

![image](https://github.com/user-attachments/assets/d6fc3d5d-7e9c-4f78-abef-aa3beb179c10)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị 11 giá trị lần lượt gồm: 01_ACHIVED_20, 02_FILLER_21, 03_TARGET_20, 04_SURPLUS_20, 05_FILLER_22, 06_BOTTOM, 07_ACHIVED_10, 08_FILLER_11, 09_TARGET_10, 10_SURPLUS_10, 11_FILLER_12 |
| 2 | AGG(sum(0)) (Rows) (từ trái sang, đầu tiên) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn to |
| 3 | AGG(sum(0)) (Rows) (từ trái sang, thứ hai) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn nhỏ (chứa KPI) |
| 4 | Measure Names (AGG(sum(0))) (Color) (từ trên xuống, đầu tiên) | Hiển thị màu sắc của 01_ACHIVED_20, 02_FILLER_21, 03_TARGET_20, 04_SURPLUS_20, 05_FILLER_22, 06_BOTTOM, 07_ACHIVED_10, 08_FILLER_11, 09_TARGET_10, 10_SURPLUS_10, 11_FILLER_12 |
| 5 | Measure Values (AGG(sum(0))) (Angle) (từ trên xuống, đầu tiên) | Hiển thị độ lớn từng phần của 01_ACHIVED_20, 02_FILLER_21, 03_TARGET_20, 04_SURPLUS_20, 05_FILLER_22, 06_BOTTOM, 07_ACHIVED_10, 08_FILLER_11, 09_TARGET_10, 10_SURPLUS_10, 11_FILLER_12 |
| 6 | KPI (AGG(sum(0))) (Text) (từ trên xuống, thứ hai) | Hiển thị giá trị KPI |
| 7 | TOTAL_CHECKS (Calculated Field) | = 286 (lượt kiểm tra) |
| 8 | TOTAL_SUCCESSFUL_CHECKS (Calculated Field) | = 140 (lượt kiểm tra thành công) |
| 9 | TOTAL_CHECKS (Calculated Field) | = 140/286 = 48.95 (%) |
| 10 | KPI (Parameter) | = 40 (%) |

### 2.10. Donut Chart - Hợp lệ

:star: **Bước 1**: Tạo 2 “Pie”, chọn “Dual Axis” để gộp 2 đường tròn thành một.

![image](https://github.com/user-attachments/assets/563d9dfc-b5b3-42d8-8d41-3d7707b499c6)

- Hình tròn bên dưới là màu xanh dương là “Rows” SUM(0).
- Hình tròn bên trên là màu trắng, kích cỡ nhỏ hơn cũng là “Rows” SUM(0).

:star: **Bước 2**: Tạo “Set” của trường REF_DATA_NM, chọn “Kiểm tra tính hợp lệ”, đặt tên set là TYPE_HOP_LE.

![image](https://github.com/user-attachments/assets/10c2ba05-7d67-4d1d-8f9c-e7687aa1ed3b)

![image](https://github.com/user-attachments/assets/ac69f3a2-fc0a-426d-941a-75cb2c98d0d0)

![image](https://github.com/user-attachments/assets/b822c346-0650-42a4-8f13-aba03809c2b0)

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_STATUSES của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra có trạng thái.

![image](https://github.com/user-attachments/assets/c87641a1-8740-481e-b7c2-a0a4744a18fb)

```sql
COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
)
```

:star: **Bước 4**: Hoàn thành “Hợp lệ”.

![image](https://github.com/user-attachments/assets/d19ed753-673c-4927-bf80-98a3ff6ab92b)

![image](https://github.com/user-attachments/assets/db508594-207d-43ba-bbb6-63e7055cc629)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị giá trị của TYPE_HOP_LE là loại Kiểm tra tính hợp lệ |
| 2 | AGG(sum(0)) (Rows) (từ trái sang, đầu tiên) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn to |
| 3 | AGG(sum(0)) (Rows) (từ trái sang, thứ hai) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn nhỏ (chứa tổng số lượt kiểm tra có trạng thái) |
| 4 | VLD_STS (AGG(sum(0))) (Color) (từ trên xuống, đầu tiên) | Hiển thị màu sắc của 3 trạng thái: Lỗi, thành công, thất bại |
| 5 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Angle) (từ trên xuống, đầu tiên) | Hiển thị độ lớn từng phần của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 6 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, đầu tiên) | Hiển thị text của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 7 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, thứ hai) | Hiển thị giá trị của TOTAL_STATUSES |

### 2.11. Donut Chart - Nhất quán

:star: **Bước 1**: Tạo 2 “Pie”, chọn “Dual Axis” để gộp 2 đường tròn thành một.

![image](https://github.com/user-attachments/assets/efdb7727-8ad2-4b71-b9fc-81c5ed76f1f6)

- Hình tròn bên dưới là màu xanh dương là “Rows” SUM(0).
- Hình tròn bên trên là màu trắng, kích cỡ nhỏ hơn cũng là “Rows” SUM(0).

:star: **Bước 2**: Tạo “Set” của trường REF_DATA_NM, chọn “Kiểm tra tính nhất quán”, đặt tên set là TYPE_NHAT_QUAN.

![image](https://github.com/user-attachments/assets/d4246364-fbc8-4e55-868f-64de1ec3941d)

![image](https://github.com/user-attachments/assets/a49dd7fe-9673-41fa-be41-902a2c6ac0aa)

![image](https://github.com/user-attachments/assets/ff863587-9525-4ce6-b6e5-6ffd802410bd)

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_STATUSES của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra có trạng thái.

![image](https://github.com/user-attachments/assets/d8d69452-ce8f-4888-a959-500f401b25a3)

```sql
COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
)
```

:star: **Bước 4**: Hoàn thành “Nhất quán”.

![image](https://github.com/user-attachments/assets/a0c5c188-4d72-49ed-b4b5-1d1875966119)

![image](https://github.com/user-attachments/assets/81a98f5e-4f0b-4d81-8bc9-9f4e2a261e0c)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị giá trị của TYPE_HOP_LE là loại Kiểm tra tính nhất quán |
| 2 | AGG(sum(0)) (Rows) (từ trái sang, đầu tiên) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn to |
| 3 | AGG(sum(0)) (Rows) (từ trái sang, thứ hai) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn nhỏ (chứa tổng số lượt kiểm tra có trạng thái) |
| 4 | VLD_STS (AGG(sum(0))) (Color) (từ trên xuống, đầu tiên) | Hiển thị màu sắc của 3 trạng thái: Lỗi, thành công, thất bại |
| 5 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Angle) (từ trên xuống, đầu tiên) | Hiển thị độ lớn từng phần của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 6 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, đầu tiên) | Hiển thị text của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 7 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, thứ hai) | Hiển thị giá trị của TOTAL_STATUSES |

### 2.12. Donut Chart - Toàn vẹn

:star: **Bước 1**: Tạo 2 “Pie”, chọn “Dual Axis” để gộp 2 đường tròn thành một.

![image](https://github.com/user-attachments/assets/d27c5365-e4dc-4463-9b08-d5779321cac7)

- Hình tròn bên dưới là màu xanh dương là “Rows” SUM(0).
- Hình tròn bên trên là màu trắng, kích cỡ nhỏ hơn cũng là “Rows” SUM(0).

:star: **Bước 2**: Tạo “Set” của trường REF_DATA_NM, chọn “Kiểm tra tính toàn vẹn”, đặt tên set là TYPE_TOAN_VEN.

![image](https://github.com/user-attachments/assets/b0d1e014-f4b7-47d1-b075-a1e953e5ce48)

![image](https://github.com/user-attachments/assets/5b913280-3f40-4cce-9326-977347a75571)

![image](https://github.com/user-attachments/assets/a201977a-4de1-4708-ac5b-3f2e15549df8)

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_STATUSES của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra có trạng thái.

![image](https://github.com/user-attachments/assets/876896a1-161d-4e46-84ce-8acf468a4810)

```sql
COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
)
```

:star: **Bước 4**: Hoàn thành “Toàn vẹn”.

![image](https://github.com/user-attachments/assets/9ceed058-41a8-42a5-84f9-3cbe9aedb069)

![image](https://github.com/user-attachments/assets/776f0af4-db3f-4484-8ed6-36ae7d726e09)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị giá trị của TYPE_HOP_LE là loại Kiểm tra tính toàn vẹn |
| 2 | AGG(sum(0)) (Rows) (từ trái sang, đầu tiên) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn to |
| 3 | AGG(sum(0)) (Rows) (từ trái sang, thứ hai) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn nhỏ (chứa tổng số lượt kiểm tra có trạng thái) |
| 4 | VLD_STS (AGG(sum(0))) (Color) (từ trên xuống, đầu tiên) | Hiển thị màu sắc của 3 trạng thái: Lỗi, thành công, thất bại |
| 5 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Angle) (từ trên xuống, đầu tiên) | Hiển thị độ lớn từng phần của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 6 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, đầu tiên) | Hiển thị text của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 7 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, thứ hai) | Hiển thị giá trị của TOTAL_STATUSES |


### 2.13. Donut Chart - Duy nhất

:star: **Bước 1**: Tạo 2 “Pie”, chọn “Dual Axis” để gộp 2 đường tròn thành một.

![image](https://github.com/user-attachments/assets/29766390-df88-492b-912b-dfe3ad3c617f)

- Hình tròn bên dưới là màu xanh dương là “Rows” SUM(0).
- Hình tròn bên trên là màu trắng, kích cỡ nhỏ hơn cũng là “Rows” SUM(0).

:star: **Bước 2**: Tạo “Set” của trường REF_DATA_NM, chọn “Kiểm tra tính duy nhất”, đặt tên set là TYPE_DUY_NHAT.

![image](https://github.com/user-attachments/assets/f3b48db2-9ea6-4eda-8989-24cf52251a0f)

![image](https://github.com/user-attachments/assets/23908a49-9a46-4a1d-ab6f-4937cecccfab)

![image](https://github.com/user-attachments/assets/61352060-05cf-4690-b8ab-e4c2c2dcb00d)

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_STATUSES của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra có trạng thái.

![image](https://github.com/user-attachments/assets/fe0c640a-8d70-4228-abb5-7ee4f38fdfff)

```sql
COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
)
```

:star: **Bước 4**: Hoàn thành “Duy nhất”.

![image](https://github.com/user-attachments/assets/48280448-142c-43d1-ac03-445cb43a451f)

![image](https://github.com/user-attachments/assets/85d5d3a5-2b37-46bf-bdb6-3292eba9c50a)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị giá trị của TYPE_DUY_NHAT là loại Kiểm tra tính duy nhất |
| 2 | AGG(sum(0)) (Rows) (từ trái sang, đầu tiên) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn to |
| 3 | AGG(sum(0)) (Rows) (từ trái sang, thứ hai) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn nhỏ (chứa tổng số lượt kiểm tra có trạng thái) |
| 4 | VLD_STS (AGG(sum(0))) (Color) (từ trên xuống, đầu tiên) | Hiển thị màu sắc của 3 trạng thái: Lỗi, thành công, thất bại |
| 5 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Angle) (từ trên xuống, đầu tiên) | Hiển thị độ lớn từng phần của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 6 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, đầu tiên) | Hiển thị text của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 7 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, thứ hai) | Hiển thị giá trị của TOTAL_STATUSES |

### 2.14. Donut Chart - Chính xác

:star: **Bước 1**: Tạo 2 “Pie”, chọn “Dual Axis” để gộp 2 đường tròn thành một.

![image](https://github.com/user-attachments/assets/9d8ba5a3-6421-4982-872d-6eae8942db56)

- Hình tròn bên dưới là màu xanh dương là “Rows” SUM(0).
- Hình tròn bên trên là màu trắng, kích cỡ nhỏ hơn cũng là “Rows” SUM(0).

:star: **Bước 2**: Tạo “Set” của trường REF_DATA_NM, chọn “Kiểm tra tính chính xác”, đặt tên set là TYPE_CHINH_XAC.

![image](https://github.com/user-attachments/assets/daf6a1ab-f9fb-4814-89ba-c27422158a2f)

![image](https://github.com/user-attachments/assets/a0a6c8c3-664a-4396-9161-e363c7bd8181)

![image](https://github.com/user-attachments/assets/83b910ca-9805-40b9-8f1b-3b9ef267115c)

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_STATUSES của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra có trạng thái.

![image](https://github.com/user-attachments/assets/2a17b175-f645-4b60-9270-77731b25ffb2)

```sql
COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
)
```

:star: **Bước 4**: Hoàn thành “Chính xác”.

![image](https://github.com/user-attachments/assets/848566b0-e550-42a0-ba32-3868b04b6218)

![image](https://github.com/user-attachments/assets/1932d50b-d142-4b96-8dbb-97bc58cb81f1)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị giá trị của TYPE_CHINH_XAC là loại Kiểm tra tính chính xác |
| 2 | AGG(sum(0)) (Rows) (từ trái sang, đầu tiên) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn to |
| 3 | AGG(sum(0)) (Rows) (từ trái sang, thứ hai) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn nhỏ (chứa tổng số lượt kiểm tra có trạng thái) |
| 4 | VLD_STS (AGG(sum(0))) (Color) (từ trên xuống, đầu tiên) | Hiển thị màu sắc của 3 trạng thái: Lỗi, thành công, thất bại |
| 5 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Angle) (từ trên xuống, đầu tiên) | Hiển thị độ lớn từng phần của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 6 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, đầu tiên) | Hiển thị text của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 7 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, thứ hai) | Hiển thị giá trị của TOTAL_STATUSES |

### 2.15. Donut Chart - Đầy đủ

:star: **Bước 1**: Tạo 2 “Pie”, chọn “Dual Axis” để gộp 2 đường tròn thành một.

![image](https://github.com/user-attachments/assets/cd87f01b-e58e-4aa9-8af4-f59fc1a8a224)

- Hình tròn bên dưới là màu xanh dương là “Rows” SUM(0).
- Hình tròn bên trên là màu trắng, kích cỡ nhỏ hơn cũng là “Rows” SUM(0).

:star: **Bước 2**: Tạo “Set” của trường REF_DATA_NM, chọn “Kiểm tra tính đầy đủ”, đặt tên set là TYPE_DAY_DU.

![image](https://github.com/user-attachments/assets/adb8c744-067a-4456-9a45-95db31cee44f)

![image](https://github.com/user-attachments/assets/ef91309b-c5fd-43bf-939c-e686fa4de67b)

![image](https://github.com/user-attachments/assets/ce334ed0-b635-4b60-8b22-a9538f632129)

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_STATUSES của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra có trạng thái.

![image](https://github.com/user-attachments/assets/984dcd9a-3343-4d02-b234-d80a76a55079)

```sql
COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
)
```

:star: **Bước 4**: Hoàn thành “Đầy đủ”.

![image](https://github.com/user-attachments/assets/02cfad7d-8edd-4332-8eb7-8ceaaf020ebe)

![image](https://github.com/user-attachments/assets/13470c3c-85c6-46f6-bb04-97b2a497ff5f)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị giá trị của TYPE_DAY_DU là loại Kiểm tra tính đầy đủ |
| 2 | AGG(sum(0)) (Rows) (từ trái sang, đầu tiên) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn to |
| 3 | AGG(sum(0)) (Rows) (từ trái sang, thứ hai) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn nhỏ (chứa tổng số lượt kiểm tra có trạng thái) |
| 4 | VLD_STS (AGG(sum(0))) (Color) (từ trên xuống, đầu tiên) | Hiển thị màu sắc của 3 trạng thái: Lỗi, thành công, thất bại |
| 5 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Angle) (từ trên xuống, đầu tiên) | Hiển thị độ lớn từng phần của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 6 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, đầu tiên) | Hiển thị text của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 7 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, thứ hai) | Hiển thị giá trị của TOTAL_STATUSES |

### 2.16. Donut Chart - Kịp thời

:star: **Bước 1**: Tạo 2 “Pie”, chọn “Dual Axis” để gộp 2 đường tròn thành một.

![image](https://github.com/user-attachments/assets/6ae5fc1e-94da-475f-9c16-980005f97023)

- Hình tròn bên dưới là màu xanh dương là “Rows” SUM(0).
- Hình tròn bên trên là màu trắng, kích cỡ nhỏ hơn cũng là “Rows” SUM(0).

:star: **Bước 2**: Tạo “Set” của trường REF_DATA_NM, chọn “Kiểm tra tính kịp thời”, đặt tên set là TYPE_KIP_THOI.

![image](https://github.com/user-attachments/assets/017ec083-0eec-4565-8d9b-a3a4512edaf1)

![image](https://github.com/user-attachments/assets/d25218e1-b6e2-47e2-96c6-4121a7a77d4c)

![image](https://github.com/user-attachments/assets/d1795f9f-0d84-4fae-a90d-7684cfff6cd2)

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_STATUSES của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra có trạng thái.

![image](https://github.com/user-attachments/assets/fa3d4a5f-1919-4e88-a5c3-e1db7e4a6ac9)

```sql
COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
)
```

:star: **Bước 4**: Hoàn thành “Kịp thời”.

![image](https://github.com/user-attachments/assets/c4a44746-ef36-4e87-9385-5aa5d61bb4fe)

![image](https://github.com/user-attachments/assets/c1f97ab0-6505-4f89-af20-e7dbd2c68917)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | Measure Names (Filters) | Lọc hiển thị giá trị của TYPE_KIP_THOI là loại Kiểm tra tính kịp thời |
| 2 | AGG(sum(0)) (Rows) (từ trái sang, đầu tiên) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn to |
| 3 | AGG(sum(0)) (Rows) (từ trái sang, thứ hai) | Hiển thị giá trị tính tổng là 0, tạo thành đường tròn nhỏ (chứa tổng số lượt kiểm tra có trạng thái) |
| 4 | VLD_STS (AGG(sum(0))) (Color) (từ trên xuống, đầu tiên) | Hiển thị màu sắc của 3 trạng thái: Lỗi, thành công, thất bại |
| 5 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Angle) (từ trên xuống, đầu tiên) | Hiển thị độ lớn từng phần của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 6 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, đầu tiên) | Hiển thị text của từng trạng thái theo giá trị của TOTAL_STATUSES |
| 7 | AGG(TOTAL_STATUSES) (AGG(sum(0))) (Text) (từ trên xuống, thứ hai) | Hiển thị giá trị của TOTAL_STATUSES |

### 2.17. Line Chart - Chất lượng dữ liệu 07 ngày gần nhất

:star: **Bước 1**: Tạo “Callculated Field” 7DAYS của trường LOG_TM. Là điều kiện hiển thị phần trăm kiểm tra thành công trong 7 ngày chỉnh sửa gần nhất trong đoạn từ FROM đến TO.

![image](https://github.com/user-attachments/assets/294b66ae-020c-4df4-a97c-99fe4d557f31)

```sql
IF [FROM] <= [TO] 
    THEN
        CASE [REPORT_TYPE]
            WHEN 'W' THEN 
                DATE([Log Tm]) >= DATETRUNC('week',[FROM],'Monday') 
                AND DATE([Log Tm]) <= DATEADD('day',-1,DATEADD('week',1,DATETRUNC('week',[FROM],'Monday')))

            WHEN 'M' THEN
                IF [TO] > DATEADD('day',-1,DATEADD('month',1,DATETRUNC('month',[FROM])))
                THEN 
                    DATE([Log Tm]) >= DATEADD('day',-6,DATEADD('day',-1,DATEADD('month',1,DATETRUNC('month',[FROM]))))
                    AND DATE([Log Tm]) <= DATEADD('day',-1,DATEADD('month',1,DATETRUNC('month',[FROM])))
                ELSE
                    IF DATEDIFF('day',DATETRUNC('month',[FROM]),{FIXED DATETRUNC('month',[FROM]):MAX([Log Tm])}) <= 6
                    THEN
                        DATE([Log Tm]) >= DATETRUNC('month',[FROM])
                        AND DATE([Log Tm]) <= {FIXED DATETRUNC('month',[FROM]):MAX([Log Tm])}
                    ELSE
                        DATE([Log Tm]) >= DATEADD('day',-6,{FIXED DATETRUNC('month',[FROM]):MAX([Log Tm])})
                        AND DATE([Log Tm]) <= {FIXED DATETRUNC('month',[FROM]):MAX([Log Tm])}
                    END
                END

            WHEN 'Y' THEN
                IF [TO] > DATEADD('day',-1,DATEADD('year',1,DATETRUNC('year',[FROM])))
                THEN 
                    DATE([Log Tm]) >= DATEADD('day',-6,DATEADD('day',-1,DATEADD('year',1,DATETRUNC('year',[FROM]))))
                    AND DATE([Log Tm]) <= DATEADD('day',-1,DATEADD('year',1,DATETRUNC('year',[FROM])))
                ELSE
                    IF DATEDIFF('day',DATETRUNC('year',[FROM]),{FIXED DATETRUNC('year',[FROM]):MAX([Log Tm])}) <= 6
                    THEN
                        DATE([Log Tm]) >= DATETRUNC('year',[FROM])
                        AND DATE([Log Tm]) <= {FIXED DATETRUNC('year',[FROM]):MAX([Log Tm])}
                    ELSE
                        DATE([Log Tm]) >= DATEADD('day',-6,{FIXED DATETRUNC('year',[FROM]):MAX([Log Tm])})
                        AND DATE([Log Tm]) <= {FIXED DATETRUNC('year',[FROM]):MAX([Log Tm])}
                    END
                END
            
            WHEN 'C' THEN
                IF DATEDIFF('day',[FROM],[TO]) <= 6 THEN
                    DATE([Log Tm]) >= [FROM]
                    AND DATE([Log Tm]) <= [TO]
                ELSE
                    DATE([Log Tm]) >= DATEADD('day',-6,[TO])
                    AND DATE([Log Tm]) <= [TO]
                END
        END
END
```

![image](https://github.com/user-attachments/assets/12897680-27b3-43c0-94a6-85f2b24a1868)

:star: **Bước 2**: Tạo “Callculated Field” TOTAL_CHECKS của trường DATA_QAL_RULE_CD. Là tính tổng số lượt kiểm tra.

![image](https://github.com/user-attachments/assets/c1b95ed1-874f-4b71-b1a6-4649d3bc55c7)

```sql
SUM(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN 1
    ELSE 0
    END
)
```

:star: **Bước 3**: Tạo “Callculated Field” TOTAL_SUCCESSFUL_CHECKS của trường VLD_STS = ‘SUCCESS’ và trường DATA_QAL_RULE_CD. Là tính tổng số lượt kiểm tra thành công.

![image](https://github.com/user-attachments/assets/96f510c0-d7d3-4cc1-b413-592d496adc13)

```sql
SUM(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    ) AND [Vld Sts] = 'SUCCESS'
    THEN 1
    ELSE 0
    END
)
```

:star: **Bước 4**: Tạo “Callculated Field” PCT_TOTAL_SUCCESSFUL_CHECKS, là tính tỷ lệ số lượt kiểm tra thành công so với tổng số lượt kiểm tra.

![image](https://github.com/user-attachments/assets/a27082ec-521a-4047-9371-5ac841caf009)

```sql
IFNULL([TOTAL_SUCCESSFUL_CHECKS] / NULLIF([TOTAL_CHECKS], 0), 0)
```

:star: **Bước 5**: Tạo “Paramater” KPI.

![image](https://github.com/user-attachments/assets/16963177-9e56-4609-9d08-4900a417445a)

![image](https://github.com/user-attachments/assets/34034391-d746-4d43-a5b3-859898707ef7)

![image](https://github.com/user-attachments/assets/eb539154-f17e-4e7c-91f3-fb5faabc02b8)

:star: **Bước 6**: Hoàn thành “Chất lượng dữ liệu 07 ngày gần nhất (thành công)”.

![image](https://github.com/user-attachments/assets/66719154-c551-4560-b604-4e126e1bd121)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | 7DAYS (Filters) | Lọc hiển thị giá trị của 7DAYS theo điều kiện từ FROM đến TO |
| 2 | DAY(LOG_TM) (Columns) | Hiển thị ngày chỉnh sửa gần nhất trên biểu đồ đường. Nằm trên trục hoành |
| 3 | AGG(PCT_TOTAL_SUCCESSFUL_CHECKS) (Rows) | Hiển thị phần trăm lượt kiểm tra thành công trên biểu đồ đường. Nằm trên trục tung |
| 4 | AGG(PCT_TOTAL_SUCCESSFUL_CHECKS) (Label) | Hiển thị giá trị phần trăm tại từng ngày trên biểu đồ đường |
| 5 | Thời gian từ (Parameter) | Giá trị FROM |
| 6 | Thời gian đến (Parameter) | Giá trị TO |

### 2.18. Bar Chart - Thống kê theo Schema

:star: **Bước 1**: Tạo “Callculated Field” TOTAL_STATUSES của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra có trạng thái.

![image](https://github.com/user-attachments/assets/e06bf2d1-091b-4a13-aef8-707ef36a6451)

```sql
COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
)
```

:star: **Bước 2**: Tạo “Callculated Field” Tổng của trường DATA_QAL_RULE_CD và trường VLD_STS. Là tính tổng số lượt kiểm tra của các trạng thái theo từng Mã schema.

![image](https://github.com/user-attachments/assets/d775049d-8492-4ba5-bc10-6c0b87f49c5a)

```sql
{ FIXED [Schm Cd] : COUNT(
    IF [Data Qal Rule Cd] IN (
        'RULE.01605',
        'RULE.01606',
        'RULE.01607',
        'RULE.01608',
        'RULE.01609',
        'RULE.01610',
        'RULE.01611',
        'RULE.01612',
        'RULE.01613',
        'RULE.01614',
        'RULE.01615'
    )
    THEN [Vld Sts]
    ELSE NULL
    END
) }
```

:star: **Bước 3**: Hoàn thành “Thống kê theo Schema”.

![image](https://github.com/user-attachments/assets/64ddc40b-e276-4edd-ab1b-ce7e1b29a625)

![image](https://github.com/user-attachments/assets/bd2f9e13-0631-41ce-bb54-697596baccba)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | VLD_STS (Columns) | Hiển thị từng trạng thái trong bảng theo cột gồm: Thất bại, thành công, lỗi |
| 2 | AGG(AVG(1)) (Columns) | Hiển thị giá trị Gantt Bar trong cột trạng thái tương ứng |
| 3 | AGG(TOTAL_STATUSES) (Columns) | Hiển thị giá trị Bar trong cột trạng thái tương ứng |
| 4 | Mã Schema (Rows) | Hiển thị giá trị Mã Schema trong bảng theo cột |
| 5 | SUM(Tổng) (Rows) | Hiển thị giá trị Tổng số lượt kiểm tra của các trạng thái theo từng Mã Schema trong bảng theo cột |
| 6 | AGG(TOTAL_STATUSES) (AGG(AVG(1))) (Label) | Hiển thị giá trị Tổng số lượt kiểm tra theo trạng thái tương ứng |
| 7 | VLD_STS (AGG(TOTAL_STATUSES)) (Color) | Hiển thị màu sắc của từng trạng thái theo cột trạng thái tương ứng |

### 2.19. Box Dashboard

![image](https://github.com/user-attachments/assets/854b8b91-562b-4d00-a486-cab0738e0bca)

### 2.20. Header Dashboard

:star: **Bước 1**: Tạo “Calculated Field” @MAX_DATE của trường LOG_TM.

![image](https://github.com/user-attachments/assets/e13ed845-cbee-430b-9d18-49445c9d5f04)

```sql
{ FIXED : MAX([Log Tm]) }
```

:star: **Bước 2**: Hoàn thành Header.

![image](https://github.com/user-attachments/assets/55ee6c35-45bf-4422-9c39-fa853e4cc27d)

| STT | LOẠI | MÔ TẢ |
| :---: | :--- | :--- |
| 1 | @MAX_DATE (Text) | Hiển thị giá trị ngày gần nhất theo ngày chỉnh sửa |

### 2.21. Dashboard

![image](https://github.com/user-attachments/assets/d4e954b7-4389-4e1d-b3ad-416f8bf8a00e)

## 3. Output

[Link Tableau Public.](https://public.tableau.com/views/DASHBOARD_DATAQUALITY_DB-Nhungdtk/Dashboard?:language=en-US&publish=yes&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)

### 3.1. By year

| STT | INPUT | INPUT VALUE |
| :---: | :--- | :--- |
| 1 | Tính chất kiểm tra | Tất cả |
| 2 | Thống kê báo cáo theo | Năm |
| 3 | Thời gian từ | 01/01/2025 |
| 4 | Thời gian đến | 29/12/2025 |

![image](https://github.com/user-attachments/assets/5f620092-cc1d-4195-a81f-bbb2d5f52db6)

### 3.2. By month

| STT | INPUT | INPUT VALUE |
| :---: | :--- | :--- |
| 1 | Tính chất kiểm tra | Tất cả |
| 2 | Thống kê báo cáo theo | Tháng |
| 3 | Thời gian từ | 01/05/2025 |
| 4 | Thời gian đến | 01/06/2025 |

![image](https://github.com/user-attachments/assets/79ed90be-4e95-4669-919c-ba1f44ae66fc)

### 3.3. By week

| STT | INPUT | INPUT VALUE |
| :---: | :--- | :--- |
| 1 | Tính chất kiểm tra | Tất cả |
| 2 | Thống kê báo cáo theo | Tuần |
| 3 | Thời gian từ | 26/05/2025 |
| 4 | Thời gian đến | 01/06/2025 |

![image](https://github.com/user-attachments/assets/b6467738-ef75-4337-83bf-c66fcfabe515)

### 3.4. By date range

| STT | INPUT | INPUT VALUE |
| :---: | :--- | :--- |
| 1 | Tính chất kiểm tra | Tất cả |
| 2 | Thống kê báo cáo theo | Tùy chọn ngày |
| 3 | Thời gian từ | 11/05/2025 |
| 4 | Thời gian đến | 22/10/2025 |

![image](https://github.com/user-attachments/assets/a4147eb6-e116-42b4-a963-ca9415d1afad)

### 3.5. By inspection type

| STT | INPUT | INPUT VALUE |
| :---: | :--- | :--- |
| 1 | Tính chất kiểm tra | Kiểm tra tính hợp lý <br> Kiểm tra tính toàn vẹn <br> Kiểm tra tính duy nhất <br> Kiểm tra tính đầy đủ |
| 2 | Thống kê báo cáo theo | Tùy chọn ngày |
| 3 | Thời gian từ | 01/01/2025 |
| 4 | Thời gian đến | 31/12/2025 |

![image](https://github.com/user-attachments/assets/aeb78b90-465b-46cd-9c97-d3c2fe5d977d)

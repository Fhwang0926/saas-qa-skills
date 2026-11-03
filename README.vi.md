# SaaS Web QA Skill

[한국어](README.md) | [English](README.en.md) | [日本語](README.ja.md) | Tiếng Việt | [Español](README.es.md) | [Português](README.pt.md) | [Français](README.fr.md) | [Deutsch](README.de.md) | [Italiano](README.it.md)

Một kỹ năng thống nhất để kiểm tra hoạt động website và SaaS, giao diện đáp ứng và khả năng tiếp cận. Kỹ năng chọn lọc và điều chỉnh quy trình từ các kỹ năng công khai của Anthropic, Vercel, Microsoft và những nguồn QA khác. Hướng dẫn và danh sách kiểm tra được đóng gói sẵn; các kỹ năng gốc và công cụ của chúng không được cài đặt kèm.

Tùy yêu cầu, kỹ năng còn hỗ trợ lập kế hoạch QA theo rủi ro, kiểm tra API, rà soát các bài kiểm thử Playwright hoặc Cypress hiện có và phân tích lỗi. Xem [nguồn và phạm vi](skills/saas-web-qa/references/sources.md).

Khi kiểm tra sau đăng nhập, kỹ năng phân biệt vai trò và không gian làm việc được phép, danh sách và bộ lọc liên quan, cùng phạm vi xác minh dữ liệu sau thay đổi. Các phiên trình duyệt riêng vẫn có thể dùng chung dữ liệu máy chủ.

Với QA theo vai trò, mười người dùng mô phỏng trải nghiệm hành trình trên trình duyệt thực. Khi môi trường hỗ trợ, các agent con thu thập phát hiện và ảnh chụp; nếu được yêu cầu sửa, các hành trình sẽ được kiểm tra lại. Xem [quy trình](skills/saas-web-qa/references/persona-journeys.md).

## Quy trình QA

- **Chẩn đoán, sửa và kiểm tra lại:** Với cả QA thông thường và theo vai trò, khi được yêu cầu sửa, agent sửa vấn đề trong phạm vi và kiểm tra lại hành vi ban đầu sau khi dịch vụ đang chạy nhận thay đổi. Nếu không thể kiểm tra lại, agent báo lý do và phần chưa xác minh.
- **Tách từng hành trình:** Khi yêu cầu nhiều chức năng, xác định điểm bắt đầu và tiêu chí thành công cho từng hành trình. QA theo vai trò ghi kết quả riêng và, với mỗi vấn đề, ghi số vai trò có thể đánh giá bước đó và số vai trò gặp lỗi. Sắp xếp theo số vai trò gặp lỗi, đồng thời nêu bật riêng các vấn đề nghiêm trọng.
- **Trước và sau đăng nhập:** Nếu đăng nhập bị chặn nhưng đã có phiên được phép, agent có thể kiểm tra riêng chức năng sau đăng nhập. Không báo toàn bộ hành trình liên tục đã thành công.

## Các kỹ năng QA công khai được tham khảo

Quy trình từ bảy kỹ năng hoặc bộ kỹ năng dưới đây được chọn lọc và điều chỉnh thành một kỹ năng `saas-web-qa`. Các gói gốc, toàn bộ quy tắc, script và công cụ không được đóng gói hoặc cài đặt. Xem [nguồn](skills/saas-web-qa/references/sources.md) để biết liên kết và phạm vi.

| Kỹ năng hoặc bộ kỹ năng | Cách kiểm tra được áp dụng |
| --- | --- |
| Anthropic `webapp-testing` | Quan sát trang đã hiển thị trước khi kiểm tra thao tác và kết quả. |
| Vercel `web-design-guidelines` | Rà soát UI, tính dễ sử dụng, tương tác và khả năng tiếp cận. |
| Microsoft `playwright-cli` | Quy trình tương tác trình duyệt và tự động hóa. |
| `qa-skills` | Lập kế hoạch theo rủi ro, QA khám phá, kiểm tra API và báo lỗi. |
| `e2e-skills` | Rà soát chất lượng kiểm thử E2E hiện có và phân tích lỗi. |
| TestDino `playwright-skill` | Kiểm thử trình duyệt bằng môi trường Playwright sẵn có của dự án. |
| `cypress-agent-skill` | Kiểm thử trình duyệt bằng môi trường Cypress sẵn có của dự án. |

## Yêu cầu agent cài đặt và thực hiện QA

Gửi yêu cầu sau cho agent lập trình. Kho lưu trữ phải được đăng lên GitHub và agent phải truy cập được.

```text
Cài kỹ năng saas-web-qa từ https://github.com/Fhwang0926/saas-qa-skills
vào dự án hiện tại, đọc hướng dẫn và thực hiện QA theo phạm vi dưới đây.
Nếu đã cài, hãy kiểm tra kỹ năng có hỗ trợ yêu cầu này trước khi dùng.

Đối tượng: trang đăng nhập của dự án hiện tại
Phạm vi: giao diện máy tính và di động, đăng nhập và khả năng tiếp cận
```

Nếu chỉ muốn cài đặt, hãy yêu cầu cài đặt mà không yêu cầu QA. Agent có thể cần phiên mới để nhận diện kỹ năng; nếu đọc được các tệp đã cài, agent có thể làm theo ngay trong phiên hiện tại.

### Hướng dẫn cho agent

1. Xác định dự án đích và agent; đọc chỉ dẫn của người dùng và dự án. Nếu đã cài `saas-web-qa`, đọc `SKILL.md` và các tài liệu liên quan để kiểm tra có hỗ trợ yêu cầu; không coi cùng tên là phiên bản mới nhất. Dùng lại nếu đủ. Nếu thiếu, kiểm tra nguồn truy cập được trong kho này, nguồn cài đặt và thay đổi cục bộ; cập nhật theo quy định mà không ghi đè nội dung không thể thay thế an toàn. Nếu cập nhật không an toàn, dùng trực tiếp hướng dẫn nguồn khi có thể. Báo rõ nếu nguồn không truy cập được hoặc thiếu chức năng.
2. Nếu cần cài, chạy lệnh bên dưới trong dự án đích. Khi không thể chọn tương tác và đã biết agent, chỉ chọn agent đó; với Codex, thêm `--agent codex -y`. Không thêm `-g` nếu người dùng không yêu cầu cài toàn cục. Tuân thủ quy định về quyền và công cụ.
3. Kiểm tra kết quả và đường dẫn cài đặt, rồi đọc `SKILL.md` và các tệp `references/` cần thiết. Nếu phiên chưa nhận diện kỹ năng nhưng đọc được tệp, hãy làm theo trực tiếp. Không chạy QA nếu chỉ được yêu cầu cài đặt.
4. Ưu tiên dịch vụ đang chạy và trình duyệt sẵn có. Tuân thủ quy định của người dùng và dự án về build, kiểm thử, khởi động server, cơ sở dữ liệu và dịch vụ ngoài. Nếu thiếu công cụ hoặc quyền truy cập, báo rõ phần đã làm và trở ngại; không tự khẳng định thành công.

## Cài đặt trực tiếp

Sau khi kho lưu trữ được đăng, chạy lệnh trong dự án đích. Cần Node.js 22.20 trở lên; chọn agent khi được hỏi.

```bash
npx skills add Fhwang0926/saas-qa-skills --skill saas-web-qa
```

Để cài từ bản sao cục bộ, thay đường dẫn bằng vị trí thực tế:

```bash
npx skills add /path/to/saas-qa-skills --skill saas-web-qa
```

Mặc định kỹ năng được cài theo dự án. Thêm `-g` để cài toàn cục. Khởi động lại agent nếu cần để nhận diện kỹ năng.

## Ví dụ sử dụng

```text
$saas-web-qa Kiểm tra trang đăng nhập trên máy tính và di động, báo cáo các lỗi có thể tái hiện.
```

### Chẩn đoán, sửa và kiểm tra lại trong một yêu cầu

```text
$saas-web-qa Kiểm tra dịch vụ đang chạy với mười vai trò người dùng mô phỏng.
Nếu có thể, dùng agent con riêng cho từng vai trò; kiểm tra trang công khai
và các chức năng chính sau đăng nhập bằng tài khoản được phép trên trình duyệt thực.
Chụp ảnh các điểm gây bối rối hoặc cản trở; với mỗi vấn đề, báo số vai trò
đã đến bước đó và số vai trò gặp lỗi. Sửa các lỗi đã xác nhận cùng một đợt,
kiểm tra lại cùng các vai trò và điều kiện, rồi báo kết quả và vấn đề còn lại.
```

Kỹ năng cung cấp hướng dẫn, không bao gồm trình duyệt, Playwright, ứng dụng đang chạy hoặc tài khoản. Kiểm tra thực tế cần môi trường và quyền truy cập phù hợp. Quy định của người dùng và dự án được ưu tiên.

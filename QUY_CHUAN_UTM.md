# Quy chuẩn UTM – Tomorrow Marketers

Quy chuẩn đặt UTM cho mọi link trỏ về website TM, áp dụng cho team Marketing, Sales và Service. Tạo link bằng [TM UTM Builder](https://tuhoang3112.github.io/utm-builder/), không gõ tay.

## Nguyên tắc chung

1. **Viết thường, không dấu, không khoảng trắng.** GA4 phân biệt hoa thường: `Fanpage_TM` và `fanpage_tm` là 2 dòng khác nhau.
2. **Phân cách bằng dấu gạch dưới:** `_` cho mọi tham số, kể cả content.
3. **Chỉ dùng mã có trong tài liệu này.** Cần mã mới thì thêm vào bảng trước, rồi mới tạo link.
4. **Không đổi mã đã dùng**, đổi mã là cắt đôi lịch sử của kênh đó.
5. **Mã organic không được chứa `cp`, `ppc` hoặc bắt đầu bằng `paid`,** nếu không GA4 sẽ xếp nhầm vào Paid.
6. **Source luôn là nền tảng thật** (`facebook`, `tiktok`, `substack`…), không đặt tên group hay tên tài khoản vào source. Tên tài khoản nằm ở medium.

## 6 tham số UTM

GA4 chỉ đọc 5 tham số chuẩn. `utm_product` và `utm_person` không hiện trong báo cáo GA4, nhưng form đã bắt vào CRM bằng hidden field, nên phân tích 2 trường này trong CRM/BigQuery.

| Tham số | Ý nghĩa | Ghi nhận ở | Ví dụ |
| --- | --- | --- | --- |
| `utm_source` | Nền tảng đưa traffic về | GA4 + CRM | `facebook` |
| `utm_medium` | Tài khoản / hình thức tiếp cận | GA4 + CRM | `group_inhouse` |
| `utm_campaign` | Chiến dịch / tuyến bài | GA4 + CRM | `thuc_hanh_doc_so` |
| `utm_content` | Bài đăng cụ thể (tiền tố + tiêu đề) | GA4 + CRM | `kien_thuc_tong_hop_metrics` |
| `utm_product` | Khóa học được nhắc đến | CRM | `pda_program` |
| `utm_person` | Nhân sự tư vấn (không bắt buộc) | CRM | `yen` |

## Bảng mã kênh

**Quy tắc đặt medium:** `<nhóm kênh>_<tài khoản>`, áp dụng cho mọi nền tảng.

- Nền tảng có nhiều loại kênh con (Facebook, Instagram): nhóm kênh là loại kênh, ví dụ `group_inhouse`, `broadcast_creativehub`.
- Nền tảng chỉ có 1 loại kênh (LinkedIn, TikTok, YouTube, Substack): nhóm kênh là tên nền tảng, ví dụ `linkedin_tm`, `tiktok_dai`.

Tên nền tảng lặp lại ở source và medium là cố ý: nhờ vậy mỗi medium là duy nhất trong toàn hệ thống, nhìn 1 cột là biết tài khoản nào. Medium vẫn ghi tài khoản kể cả khi nền tảng hiện chỉ có 1 tài khoản, để mở thêm tài khoản không phải đổi quy tắc.

| `utm_source` | `utm_medium` | Tài khoản | Loại kênh |
| --- | --- | --- | --- |
| facebook | `fanpage_tm` | Tomorrow Marketers Academy | Fanpage |
| facebook | `fanpage_tm_community` | Tomorrow Marketers Academy (team Community) | Fanpage |
| facebook | `fanpage_ba` | Data & AI Strategy | Fanpage |
| facebook | `fanpage_tmai` | TM AI Academy | Fanpage |
| facebook | `group_inhouse` | 500 anh em Marketing Inhouse | Group |
| facebook | `group_bc` | Business & Marketing Case | Group |
| facebook | `group_strategy` | Brand Strategy & Business Growth Hub | Group |
| facebook | `group_connect` | Group cựu học viên | Group |
| facebook | `broadcast_case` | Case Playground @TM | Broadcast |
| facebook | `broadcast_data` | Data & AI Strategy @TM | Broadcast |
| facebook | `broadcast_mktworld` | Marketing World @TM | Broadcast |
| facebook | `broadcast_growth` | Strategy & Growth @TM | Broadcast |
| instagram | `instagram_tm` | tomorrow.marketers | Profile |
| instagram | `broadcast_creativehub` | TM Creative Hub | Broadcast |
| tiktok | `tiktok_tma` | Tomorrow Marketers Academy | TikTok |
| tiktok | `tiktok_dai` | Data AI không drama | TikTok |
| tiktok | `tiktok_zoe` | Tóc Hồng Giải Mã – Zoe (cá nhân) | TikTok |
| youtube | `youtube_tma` | Tomorrow Marketers Academy | YouTube |
| youtube | `youtube_zoe` | Tóc Hồng Giải Mã – Zoe (cá nhân) | YouTube |
| linkedin | `linkedin_tm` | Tomorrow Marketers | LinkedIn |
| linkedin | `linkedin_data` | Data & AI Strategy | LinkedIn |
| linkedin | `linkedin_zoe` | Zoe (cá nhân) | LinkedIn |
| substack | `substack_analytics` | Analytics & AI Strategy | Substack |
| substack | `substack_career` | Career Guide | Substack |
| substack | `substack_strategy` | Strategy & Growth | Substack |
| substack | `substack_zoe` | Zoe (cá nhân) | Substack |
| email | `email_newsletter` | Email newsletter, email bán hàng (ActiveCampaign) | Email |
| email | `email_automation` | Chuỗi email tự động, kể cả chuỗi gửi sau khi tải ebook | Email |
| ebook | `ebook_ldp` | Link trên landing page ebook | Ebook |
| ebook | `ebook_pdf` | Link trong file ebook | Ebook |
| blog | `anchor_text` | Blog TM: link chữ trong bài | Blog |
| blog | `banner` | Blog TM: ảnh trong bài | Blog |
| blog | `bottom_banner` | Blog TM: banner cuối bài | Blog |
| facebook / tiktok / google | `cpc` | Quảng cáo trả tiền | Paid |

## Lưu ý cho Paid & Blog

**Paid**

- Medium luôn là `cpc`, không ghi tài khoản. Source là nền tảng chạy ads: `facebook`, `tiktok`, `google`.
- `utm_content` là tiêu đề nội dung quảng cáo.
- Bài sales trên fanpage khi đẩy sang chạy ads: đổi medium sang `cpc` trước khi chạy. Nếu không, traffic trả tiền sẽ bị tính vào organic.

**Blog**

- Medium là vị trí đặt link trong bài: `anchor_text` (link chữ), `banner` (ảnh trong bài), `bottom_banner` (banner cuối bài). Chỉ có 1 blog nên không cần mã tài khoản.

## Sales & Service

Source là kênh gửi link, medium là tên team (`sales` / `service`). Link luôn kèm `utm_product`, `utm_person` không bắt buộc. Không cần campaign và content.

| Tình huống | `utm_source` | `utm_medium` |
| --- | --- | --- |
| Lead từ các nguồn của Sales | facebook / instagram / zalo / email | `sales` |
| Lead từ các nguồn của Service | facebook / instagram / zalo / group_connect / circle / email | `service` |

## Campaign, content, product

**`utm_campaign` = chiến dịch hoặc tuyến bài**, cách nhau bằng `_`: `promotion_tet`, `case_playlist`, `career_hub`, `marketing_nganh_hang`, `thuc_hanh_doc_so`, `review_cv_with_tm`. Bài không thuộc tuyến nào để trống.

**`utm_content` = `[vị trí]_<loại nội dung>_<tiêu đề>`**, cách nhau bằng `_`, tiêu đề tối đa 5–6 từ.

| Tiền tố | Dùng cho | Ví dụ |
| --- | --- | --- |
| `sales` | Bài bán khóa học | `sales_khong_con_so_doc_so` |
| `distribution_link` | Bài phân phối link | `distribution_link_data_analyst_roadmap` |
| `kien_thuc` | Bài kiến thức | `kien_thuc_tong_hop_metrics` |
| `testimonial` | Cảm nhận học viên | `testimonial_tuhoang` |
| `creative` | Bài sáng tạo, viral | `creative_dan_data_noi_gi` |
| `news`, `countdown`, `event` | Tin tức, đếm ngược, sự kiện | `countdown_early_bird` |
| `bio` | Vị trí: link cố định ở bio (TikTok, YouTube, Instagram). Không gắn với bài cụ thể nên chỉ ghi `bio` | `bio` |
| `description` | Vị trí: link trong phần mô tả video YouTube. Đứng trước loại nội dung | `description_kien_thuc_bcg_matrix` |
| `cmt` | Vị trí: link trong comment, mọi nền tảng. Đứng trước loại nội dung | `cmt_sales_khong_con_so_doc_so` |
| `story` | Vị trí: link qua sticker trên Story Instagram / Facebook. Đứng trước loại nội dung | `story_countdown_early_bird` |

Link nằm trong thân bài / caption là mặc định, không ghi vị trí. Chỉ ghi vị trí khi link nằm chỗ khác (bio, description, cmt, story). Link ở mục giới thiệu trang, Featured hoặc trang kênh tính là `bio`; comment ghim tính là `cmt`. TikTok chỉ có link ở bio, nên link TikTok luôn là `bio`.

Tiền tố mới ngoài danh sách thì thêm vào bảng này trước khi dùng.

**`utm_product` = mã khóa học:**

| Nhóm | Khóa học | Mã |
| --- | --- | --- |
| Marketing | Marketing Foundation | `marketing_foundation` |
| Marketing | AI Digital Marketing | `digital_foundation` |
| Marketing | Performance Marketing | `digital_performance` |
| Marketing | Content Marketing | `content_marketing` |
| Marketing | Advanced AI Marketer | `advanced_ai_marketer` |
| Marketing | Digital Marketing Manager Program | `dmm_program` |
| Sinh viên (Case/MT) | Case Mastery | `case_mastery` |
| Executive Education | Brand Development | `brand_development` |
| Executive Education | Consumer Psychology | `consumer_psychology` |
| Executive Education | Strategy Formulation | `strategy_formulation` |
| Executive Education | Decision Science | `decision_science` |
| Executive Education | AI CEO Program | `ceo_program` |
| Executive Education | CMO Program | `cmo_program` |
| TM AI | Generative & Agentic AI | `generative_ai` |
| TM AI | AI Marketing | `ai_marketing` |
| TM AI | Transform Organization with AI | `transform_ai` |
| TM AI | AI Marketing & Sales System | `ai_marketing_sales_system` |
| TM AI | AI Professional Program | `ai_program` |
| TM AI | AI Kids – Bách Khoa | `ai_kids` |
| Data | Power BI & AI for Data Analytics | `data_analysis` |
| Data | Excel & AI for Data Analytics | `excel` |
| Data | Analytics for Strategy | `analytics_for_strategy` |
| Data | Database Systems for AI & Automation | `sql` |
| Data | AI & Machine Learning with Python | `python` |
| Data | Professional Data Analyst Program | `pda_program` |

Khóa mới: lấy tên đầy đủ, viết thường, cách nhau bằng `_`, rồi thêm vào danh sách.

## Ví dụ link hoàn chỉnh

`…` là `https://www.tomorrowmarketers.org`.

| Tình huống | Link |
| --- | --- |
| Bài kiến thức trong group 500 anh em, tuyến "Thực hành đọc số" | `…/data-school?utm_source=facebook&utm_medium=group_inhouse&utm_campaign=thuc_hanh_doc_so&utm_content=kien_thuc_tong_hop_metrics&utm_product=pda_program` |
| Link bio TikTok Data AI không drama | `…/data-school?utm_source=tiktok&utm_medium=tiktok_dai&utm_content=bio&utm_product=pda_program` |
| Bài Substack cá nhân của Zoe | `…/data-school?utm_source=substack&utm_medium=substack_zoe&utm_content=kien_thuc_he_thong_data_marketing&utm_product=pda_program` |
| Broadcast Data & AI Strategy | `…/data-school?utm_source=facebook&utm_medium=broadcast_data&utm_content=countdown_early_bird&utm_product=pda_program` |
| Facebook Ads | `…/data-school?utm_source=facebook&utm_medium=cpc&utm_content=khong_con_so_doc_so&utm_product=pda_program` |
| Sale gửi link qua inbox Facebook | `…/data-school?utm_source=facebook&utm_medium=sales&utm_product=pda_program&utm_person=yen` |

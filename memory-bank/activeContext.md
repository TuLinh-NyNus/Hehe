# Active Context

## Current Focus

Hiện tại đang tập trung vào việc phân tích yêu cầu và lập kế hoạch chi tiết cho tính năng mới: Trang Đề Thi. Kế hoạch này sẽ bao gồm thiết kế cơ sở dữ liệu, xác định các API backend cần thiết và phác thảo cấu trúc frontend.

## Recent Completions

(Chưa có)

## Implementation Details

(Chưa có chi tiết triển khai)

## Recent Activities
- Initialized Level 4 workflow for codebase scanning.
- Verified core directory structure.
- Fetched relevant coding rules and workflow guidelines.
- Reviewed `productContext.md` and `projectbrief.md`.
- Added initial task entry to `tasks.md`.

## Implementation Plan (Initial)
1.  Define criteria for "duplicate" and "misplaced" files/components through a Creative Phase.
2.  Obtain a detailed map of the current codebase structure.
3.  Analyze the structure against the defined criteria and coding rules.
4.  Identify and list potential duplicate or misplaced items.
5.  Summarize findings in a report.

## Open Questions/Blockers
- None currently.

# Ngữ cảnh hiện tại của dự án

## Tổng quan dự án
NyNus là nền tảng học tập trực tuyến cung cấp trải nghiệm học tập cá nhân hóa bằng cách sử dụng AI. Giúp học sinh, sinh viên và người đi làm tiếp cận kiến thức mới một cách hiệu quả, thông qua các khóa học tương tác và công cụ học tập thông minh.

## Trạng thái hiện tại
Dự án đang ở giai đoạn thiết lập nền tảng ban đầu. Backend cơ bản đã được thiết lập với NestJS 11.0.13, Prisma và PostgreSQL. Cấu trúc dự án đã được tổ chức theo mô hình monorepo sử dụng Turborepo.

## Quyết định kỹ thuật gần đây
- Xác nhận sử dụng PostgreSQL làm database duy nhất cho dự án
- Chọn monorepo với Turborepo để quản lý các packages
- Chuẩn hóa việc sử dụng pnpm 7.24.2 cụ thể để đảm bảo tương thích
- Cập nhật NestJS lên phiên bản 11.0.13 để có tương thích với Swagger
- Thiết kế schema database với Prisma cho các entity chính: User, Course, Lesson, Enrollment, Category và Assessment

## Công việc đang tiến hành
- Tiếp tục phát triển các module backend (Courses, Lessons, Categories)
- Chuẩn bị thiết lập PostgreSQL server cho việc migration
- Chuẩn bị triển khai ứng dụng frontend với Next.js
- Hoàn thiện tài liệu API với Swagger

## Thách thức hiện tại
- Thiết lập PostgreSQL server cho development
- Đảm bảo tính nhất quán của môi trường phát triển giữa các thành viên team
- Thiết lập quy trình CI/CD hiệu quả
- Xây dựng kiến trúc database đủ linh hoạt cho nhu cầu mở rộng trong tương lai

## Ưu tiên ngắn hạn
1. Thiết lập PostgreSQL server cho development
2. Thực hiện initial migration cho Prisma schema
3. Phát triển các module backend còn lại
4. Thiết lập ứng dụng frontend cơ bản với Next.js

## Thay đổi gần đây
- Hoàn thành thiết lập cơ bản cho backend với NestJS, Prisma và PostgreSQL
- Tạo các custom exception classes và global exception filter
- Cấu hình Winston logger cho toàn bộ ứng dụng
- Phát triển User module với đầy đủ CRUD operations
- Cấu hình Swagger cho API documentation

## Current Focus
- ✓ Thiết lập PostgreSQL server cho development
- ✓ Phát triển Course module và các module liên quan
- ✓ Xử lý các thách thức về kết nối database và migration
- Tạo authentication và authorization module
- ✓ Cải thiện cấu trúc dự án để đảm bảo tính nhất quán

### MapIDController Implementation

Đang triển khai MapIDController với các endpoints:
- GET /map-id/structure - Lấy cấu trúc MapID
- GET /map-id/parse/:questionId - Phân giải QuestionID thành các thành phần
- POST /map-id/generate - Tạo QuestionID từ các thành phần

Sử dụng MapIDService đã được triển khai trước đó với các phương thức:
- parseQuestionId
- generateQuestionId
- validateQuestionId
- getQuestionIdDescription
- getMapIdStructure

Triển khai này tuân theo yêu cầu từ Question.md về cấu trúc QuestionID:
- QuestionID có cấu trúc [Lớp Môn Chương Mức_độ Bài] cho ID5
- QuestionID có cấu trúc [Lớp Môn Chương Mức_độ Bài-Dạng] cho ID6
- Mỗi thành phần là 1 ký tự số [0-9] hoặc chữ cái in hoa [A-Z]

## Recent Issues
1. PostgreSQL Connection:
   - ✓ Đã giải quyết: Thiết lập thành công PostgreSQL server với Docker
   - ✓ Đã giải quyết: Cập nhật thông tin kết nối trong file .env

2. Prisma Migration:
   - ✓ Đã giải quyết: Thực hiện migration thành công cho Course và Enrollment schema
   - ✓ Đã giải quyết: Tạo Prisma client types

## Recent Achievements
- Đã thiết lập PostgreSQL server với Docker
- Đã thực hiện migration cho Course, Enrollment và các models liên quan
- Đã cập nhật Prisma schema với đầy đủ các mối quan hệ (relations)
- Đã hoàn thành việc tạo Prisma client types
- Đã hoàn thành việc xây dựng Repository Interfaces cho module Question (IQuestionRepository, IQuestionVersionRepository, IQuestionImageRepository, IQuestionTagRepository)

## Pending Tasks
1. PostgreSQL Setup:
   - [ ] Thiết lập PostgreSQL server cho development
   - [ ] Cập nhật database connection string trong .env
   - [ ] Thực hiện initial migration

2. Course Module:
   - [ ] Tạo DTO classes cho Course
   - [ ] Tạo CourseService với các phương thức CRUD
   - [ ] Tạo CourseController với API endpoints
   - [ ] Tích hợp với Category và User modules

3. Authentication:
   - [ ] Tạo AuthModule cho xác thực
   - [ ] Implement JWT authentication
   - [ ] Tạo Guards cho authorization
   - [ ] Cấu hình role-based access control

## Thiết lập Users Module
User module đã được phát triển thành công với:

### UserDTO và Entity
```typescript
// CreateUserDto
export class CreateUserDto {
  @ApiProperty({ description: 'Email address của người dùng' })
  @IsEmail()
  @IsNotEmpty()
  email: string;

  @ApiProperty({ description: 'Mật khẩu của người dùng (tối thiểu 6 ký tự)' })
  @IsString()
  @IsNotEmpty()
  @MinLength(6)
  password: string;

  @ApiProperty({ description: 'Tên của người dùng' })
  @IsString()
  @IsNotEmpty()
  firstName: string;

  @ApiProperty({ description: 'Họ của người dùng' })
  @IsString()
  @IsNotEmpty()
  lastName: string;

  @ApiProperty({ description: 'Vai trò của người dùng' })
  @IsEnum(UserRole)
  role?: UserRole;
}
```

### UserService với CRUD
Service với đầy đủ các phương thức CRUD và xử lý password hashing:
- create: Tạo user mới và hash password
- findAll: Lấy danh sách users (không bao gồm password)
- findOne: Tìm user theo ID
- update: Cập nhật thông tin user
- remove: Xóa user
- findByEmail: Tìm user theo email (cho authentication)

### UserController với API endpoints
Controller với đầy đủ các endpoint và Swagger documentation:
- POST /users: Tạo user mới
- GET /users: Lấy danh sách users
- GET /users/:id: Lấy thông tin một user
- PATCH /users/:id: Cập nhật thông tin user
- DELETE /users/:id: Xóa user

## Error Handling và Logging
Đã thiết lập hệ thống xử lý lỗi và logging:

### Custom Exceptions
- ResourceNotFoundException: Xử lý trường hợp không tìm thấy resource
- ValidationException: Xử lý lỗi validation

### GlobalExceptionFilter
Filter xử lý tất cả các loại exception:
- HttpException: Các exception từ NestJS
- PrismaClientKnownRequestError: Lỗi từ Prisma client
- Error: Các lỗi khác

### Winston Logger
Cấu hình Winston logger với các transports:
- Console: Logs với màu sắc và formatting
- File: Error logs riêng và combined logs
- Các level khác nhau tùy theo môi trường (development/production)

## Next Steps
1. Thiết lập PostgreSQL server và thực hiện migration
2. Phát triển Course module và các module liên quan
3. Tạo AuthModule và implement authentication
4. Thiết lập ứng dụng frontend với Next.js

### Thiết lập backend cơ bản

#### Tiến trình hiện tại
- [X] Khởi tạo dự án NestJS
- [X] Cấu hình PostgreSQL bằng Prisma
- [X] Thiết lập validation sử dụng class-validator
- [X] Thiết lập xử lý lỗi và logging
- [X] Tạo các module cơ bản cho Users

#### Hoạt động gần đây
1. Cài đặt và cấu hình Prisma với PostgreSQL
   - Cài đặt Prisma CLI v5.2.0
   - Tạo schema.prisma với các models: User, Course, Lesson, Enrollment, Progress, Category, Assessment
   - Tạo và áp dụng migration đầu tiên thành công
   - Khởi tạo PrismaModule và PrismaService để quản lý kết nối

2. Cấu hình và khởi động PostgreSQL với Docker
   - Tạo file docker-compose.yml cho PostgreSQL v15
   - Giải quyết vấn đề không tương thích giữa PostgreSQL v14 và v15
   - Tạo database "nynus_db" với user và password "admin"

3. Thiết lập xử lý lỗi và logging
   - Tạo GlobalExceptionFilter để xử lý lỗi NestJS và Prisma
   - Cấu hình logging sử dụng Winston
   - Đơn giản hóa logging để tránh lỗi với winston-daily-rotate-file

4. Thay thế bcrypt bằng bcryptjs
   - Cài đặt bcryptjs để tránh lỗi build với native bcrypt
   - Cập nhật UserService để sử dụng bcryptjs

#### Thử thách đã giải quyết
1. Lỗi không tương thích giữa dữ liệu PostgreSQL v14 và container v15
   - Giải pháp: Xóa volume cũ và tạo mới
   
2. Lỗi với winston-daily-rotate-file
   - Giải pháp: Đơn giản hóa logging để chỉ sử dụng Console transport
   
3. Lỗi build với native bcrypt
   - Giải pháp: Thay thế bằng bcryptjs (phiên bản JavaScript thuần)

#### Trạng thái hiện tại
- Ứng dụng NestJS chạy thành công trên cổng 3001
- Swagger UI có sẵn tại http://localhost:3001/api/docs
- Các endpoints cho User module đã được tạo và hoạt động
- Docker container PostgreSQL chạy thành công trên cổng 5432
- Database schema đã được tạo thông qua Prisma migration

#### Bước tiếp theo
1. Tạo các repository và service cho các module còn lại:
   - Course, Lesson, Enrollment, Progress, Category và Assessment
2. Triển khai xác thực và phân quyền
3. Thêm logic nghiệp vụ cho các module
4. Viết test

#### Thông tin kỹ thuật
- NestJS v11.0.13
- Prisma v5.2.0 với PostgreSQL
- Docker với PostgreSQL v15
- Validation: class-validator v0.14.0
- Winston logger (Console transport)
- Swagger UI cho API documentation

## Nhiệm vụ hiện tại: Cấu hình Prisma schema cho Course và liên kết

### Tổng quan
Tôi đang tiến hành cấu hình Prisma schema cho Course và các mối quan hệ liên quan. Đây là một nhiệm vụ cấp độ 4 (Complex System) vì nó ảnh hưởng đến kiến trúc dữ liệu cốt lõi và có tác động đến nhiều phần của hệ thống.

### Phạm vi công việc
- Tạo model Course trong prisma/schema.prisma
- Tạo các quan hệ với User, Category
- Migrate database
- Tạo Prisma client types

### Phân tích hiện trạng
- File schema.prisma đã tồn tại và có các định nghĩa cơ bản cho Course, User, Category
- Tuy nhiên, cần điều chỉnh để phù hợp với entity Course hiện tại trong packages/entities
- Entity Course hiện tại có các trường không có trong schema.prisma
- Cần đảm bảo tính nhất quán giữa entity và schema

### Thách thức
- Đảm bảo schema phù hợp với entity trong packages/entities
- Xử lý các mối quan hệ phức tạp (many-to-many, one-to-many)
- Tránh gây gián đoạn cho dữ liệu hiện có trong database
- Tạo migration an toàn

### Kế hoạch
1. Cập nhật model Course trong schema.prisma để phản ánh entity
2. Tạo/cập nhật các quan hệ với User (instructor) và Category
3. Tạo migration và áp dụng vào database
4. Cập nhật Prisma client types
5. Cập nhật tasks.md để đánh dấu hoàn thành

### Cải thiện Cấu trúc Dự án
Đã thực hiện cải thiện cấu trúc dự án để đảm bảo tính nhất quán và tuân thủ best practices:

#### Nhiệm vụ 9.1: Làm rõ cấu trúc
- Đã phân tích và kiểm tra thư mục packages/packages
- Đã thống nhất cấu trúc module trong apps/api
- Đã đề xuất cấu trúc module chuẩn để đảm bảo tính nhất quán

#### Nhiệm vụ 9.2: Xử lý issues phát hiện sau cải thiện cấu trúc
- Đã kiểm tra và sửa lỗi export/import trong package `@project/database`
- Đã cập nhật file barrel exports (index.ts) để re-export các interfaces từ `@project/interfaces`
- Đã sửa module imports trong các modules bị ảnh hưởng, cụ thể:
  - Thay thế `PrismaModule` bằng `DatabaseModule` trong LessonsModule
  - Đảm bảo các repository interfaces được import đúng cách
- Đã kiểm tra lại build process và xác nhận không còn lỗi
- Đã kiểm tra linter và đảm bảo không có lỗi linter

Kết quả:
- Toàn bộ dự án build thành công (npm run build)
- Không có lỗi linter (npm run lint)
- Cấu trúc dự án đã được cải thiện và nhất quán hơn
- Đảm bảo tính module hóa và tái sử dụng code tốt hơn

## Tối ưu hóa Database Schema

Sau khi đánh giá schema.prisma hiện tại của dự án, đã phát hiện các điểm cần cải thiện để phù hợp hơn với yêu cầu của một hệ thống giáo dục trực tuyến:

### Đánh giá Schema hiện tại

1. **Model User và UserProfile**:
   - Đã có cấu trúc cơ bản tốt với UserRole và các quan hệ
   - Thiếu các trường quan trọng như status, lastLogin
   - UserProfile đã lưu socialLinks và preferences dạng Json, phù hợp cho dữ liệu linh hoạt

2. **Model Course và Lesson**:
   - Course có nhiều metadata hữu ích (price, duration, prerequisites, learningOutcomes)
   - Lesson khá đơn giản, cần bổ sung thêm thông tin như duration, attachments, videoUrl
   - Chưa có hỗ trợ đa ngôn ngữ cho nội dung khóa học

3. **Model Enrollment và Progress**:
   - Đã có cấu trúc theo dõi tiến độ cơ bản
   - Thiếu tracking chi tiết về thời gian học tập (timeSpent)
   - Chưa có liên kết với thanh toán và chứng chỉ

4. **Các Model khác**:
   - Category đã có self-reference cho hierarchical structure
   - Assessment và Question chưa đủ chi tiết cho các bài kiểm tra phức tạp
   - Thiếu các models quan trọng như Review, Payment, Certificate

5. **Indices và Performance**:
   - Thiếu indices cho nhiều truy vấn phổ biến
   - Cấu trúc Json cho một số trường có thể ảnh hưởng đến khả năng tìm kiếm

### Đề xuất cải thiện

1. **Thêm Models mới**:
   - Payment: quản lý các giao dịch thanh toán
   - Certificate: cấp và quản lý chứng chỉ hoàn thành
   - Review: đánh giá và nhận xét khóa học
   - Notification: hệ thống thông báo
   - QuizResult: kết quả chi tiết cho các bài kiểm tra

2. **Cải thiện Models hiện có**:
   - User: thêm status, lastLogin
   - Course: thêm slug, metaTitle, metaDescription cho SEO
   - Lesson: thêm duration, videoUrl, attachments
   - Progress: thêm timeSpent, score
   - Enrollment: thêm liên kết đến Payment, Certificate

3. **Hỗ trợ đa ngôn ngữ**:
   - Thêm model CourseTranslation cho nội dung khóa học đa ngôn ngữ
   - Thiết kế quan hệ hiệu quả giữa Course và các bản dịch

4. **Tối ưu Indices**:
   - Thêm indices cho các truy vấn phổ biến như tìm kiếm khóa học, lọc theo danh mục
   - Tạo composite indices cho các truy vấn joins phức tạp
   - Đảm bảo tất cả foreign keys đều có indices

5. **Cải thiện Data Types**:
   - Sử dụng @db.Text cho các trường nội dung dài
   - Chuyển đổi một số trường từ String[] sang Json khi phù hợp
   - Thêm constraints và validations phù hợp

### Cải thiện Repository Pattern

Đề xuất cải thiện cấu trúc repository pattern hiện tại:

1. **Base Repository Interface**:
   - Tạo interface chung cho các operations CRUD cơ bản
   - Hỗ trợ pagination, filtering, và ordering tiêu chuẩn
   - Định nghĩa rõ return types với generics

2. **Transaction Support**:
   - Cải thiện hỗ trợ transaction qua repository
   - Tạo helper functions cho việc thực thi trong transaction

3. **Business Methods**:
   - Mở rộng các repository interfaces với business methods cụ thể
   - Ví dụ: findPopularCourses, updateAverageRating, findRecommendedCourses

4. **Abstraction Layers**:
   - Tách biệt rõ ràng giữa entity models và persistence models
   - Sử dụng mapper functions để chuyển đổi giữa các layers

Các cải tiến này sẽ tạo nền tảng vững chắc cho việc phát triển tính năng AI và cá nhân hóa trong tương lai, đồng thời cải thiện hiệu suất và khả năng mở rộng của hệ thống.

## Tính năng AI & Cá nhân hóa

Đã hoàn thành Task 11.3: Thiết kế cấu trúc dữ liệu AI.

### Các thành phần đã triển khai
1. **Models Prisma**:
   - `UserActivityLog`: Theo dõi hoạt động người dùng (xem khóa học, hoàn thành bài học, tìm kiếm...)
   - `UserLearningStyle`: Lưu trữ phong cách học tập (visual, auditory, kinesthetic...)
   - `UserInterest`: Lưu trữ mối quan tâm của người dùng với các danh mục
   - `ContentRecommendation`: Lưu trữ các đề xuất nội dung cho người dùng
   - `LearningPath`: Lộ trình học tập được cá nhân hóa

2. **Entities**:
   - Đã tạo các entity classes tương ứng trong package `@project/entities`
   - Các entity sử dụng các kiểu dữ liệu rõ ràng và có mối quan hệ với nhau

3. **Repository Interfaces**:
   - Đã thiết kế các repository interfaces với các phương thức CRUD và truy vấn cụ thể
   - Sử dụng các kiểu dữ liệu chính xác, tránh sử dụng `any` không cần thiết

### Kiểm tra linter
- Đã chạy ESLint cho các repository interfaces và entity classes
- Không có lỗi linter liên quan đến việc sử dụng `any` không cần thiết
- Có các cảnh báo về `strictPropertyInitialization` đây là bình thường trong các entity classes

Bước tiếp theo là thiết kế API cho các tính năng AI và cá nhân hóa (Task 11.4).

## Task 11.4 - Thiết kế API cho tính năng AI

Đang thực hiện thiết kế API endpoints cho tính năng AI và cá nhân hóa. Tập trung vào:

1. **API cho User Activity Tracking**:
   - Cần endpoint để ghi lại các hoạt động của người dùng
   - Thiết kế cấu trúc request/response chuẩn
   - Xác định các loại events cần track

2. **API cho Learning Style Assessment**:
   - Endpoint để cập nhật và truy vấn learning style
   - Cơ chế để tính toán và cập nhật learning style dựa trên hành vi

3. **API cho Recommendations**:
   - Endpoint để lấy các gợi ý khóa học phù hợp với người dùng
   - Hỗ trợ filtering và sorting cho kết quả gợi ý

4. **API cho Learning Paths**:
   - Endpoints để tạo và quản lý lộ trình học tập cá nhân hóa
   - Tích hợp với dữ liệu interests và learning styles

5. **Response Format**:
   - Thiết kế cấu trúc response chuẩn cho các tính năng AI
   - Đảm bảo bao gồm metadata cần thiết cho frontend

### Tiến trình

Đã thiết kế các DTOs và Controllers cho tính năng AI và cá nhân hóa:

#### DTOs đã tạo:
1. **CreateUserActivityDto**:
   - Ghi lại hoạt động người dùng với các loại sự kiện (xem khóa học, hoàn thành bài học, tìm kiếm...)
   - Bao gồm metadata linh hoạt cho thông tin bổ sung

2. **UpdateLearningStyleDto**:
   - Cập nhật điểm số cho các phong cách học tập khác nhau
   - Hỗ trợ visualScore, auditoryScore, kinestheticScore, readingWritingScore, logicalScore, socialScore, solitaryScore

3. **GetRecommendationsDto**:
   - Lấy gợi ý với nhiều loại (cá nhân hóa, khóa học tương tự, xu hướng...)
   - Hỗ trợ phân trang và lọc theo danh mục

4. **CreateLearningPathDto**:
   - Tạo lộ trình học tập với danh sách khóa học và metadata
   - Hỗ trợ nhiều loại lộ trình khác nhau (nghề nghiệp, kỹ năng, học thuật...)

#### Controllers đã tạo:
1. **UserActivityController**:
   - POST `/user-activity` - Ghi lại hoạt động người dùng
   - GET `/user-activity/my-activities` - Lấy lịch sử hoạt động của người dùng hiện tại
   - GET `/user-activity/users/:userId` - Lấy hoạt động của người dùng cụ thể (Admin)

2. **RecommendationController**:
   - GET `/recommendations` - Lấy gợi ý cá nhân hóa cho người dùng đã đăng nhập
   - GET `/recommendations/public` - Lấy gợi ý cho người dùng chưa đăng nhập
   - GET `/recommendations/similar-to/:courseId` - Lấy khóa học tương tự
   - GET `/recommendations/trending` - Lấy khóa học xu hướng

3. **LearningPathController**:
   - POST `/learning-paths` - Tạo lộ trình học tập mới
   - GET `/learning-paths` - Lấy danh sách lộ trình
   - GET `/learning-paths/:id` - Lấy chi tiết lộ trình
   - PATCH `/learning-paths/:id` - Cập nhật lộ trình
   - DELETE `/learning-paths/:id` - Xóa lộ trình
   - GET `/learning-paths/user/my-paths` - Lấy lộ trình của người dùng hiện tại

Tất cả các endpoints đã được thiết kế với định dạng response chuẩn, metadata phù hợp và hỗ trợ phân trang. Đảm bảo tính bảo mật với JWT authentication và permission checking khi cần thiết.

### Kết quả

Task 11.4 đã được hoàn thành với kết quả như sau:

1. **Tạo thành công cấu trúc module cho AI Features**:
   - Cấu trúc folder chuẩn NestJS với controllers, dtos
   - File barrel exports để quản lý imports dễ dàng
   - Module NestJS để tích hợp với ứng dụng chính

2. **Thiết kế đầy đủ DTOs cho tất cả tính năng AI**:
   - CreateUserActivityDto: tracking hoạt động người dùng
   - UpdateLearningStyleDto: cập nhật phong cách học tập
   - GetRecommendationsDto: lấy gợi ý khóa học
   - CreateLearningPathDto: tạo lộ trình học tập

3. **Thiết kế đầy đủ controllers với các endpoints API**:
   - UserActivityController: endpoints cho tracking hoạt động
   - RecommendationController: endpoints cho gợi ý khóa học
   - LearningPathController: endpoints cho lộ trình học tập

4. **Kết quả kiểm tra linter**:
   - Không có lỗi linter trong các DTOs (đã kiểm tra với `eslint --max-warnings=0`)
   - Đã sửa lỗi imports không tồn tại trong controllers (sẽ được xử lý khi implement)
   - Đã sửa lỗi tham số không sử dụng bằng cách thêm prefix _

API được thiết kế tuân thủ REST conventions và sử dụng các decorator NestJS chuẩn. Tất cả đều có documentation đầy đủ với Swagger decorators và được tổ chức theo domain model rõ ràng. Việc thiết kế API hoàn chỉnh này tạo nền tảng vững chắc cho việc implement các tính năng AI và cá nhân hóa trong hệ thống.

## Nhiệm vụ hiện tại: Module Exam

### Tổng quan
Đang triển khai Module Exam để quản lý bài thi, câu hỏi và kết quả thi. Đã hoàn thành các phần:
- Cập nhật Prisma Schema và Migration cho module Exam
- Tạo các Entity Classes cho Exam, ExamResult, ExamQuestion
- Tạo các DTO Classes cho module Exam
- Tạo các Repository Interfaces cho module Exam

### Đã hoàn thành
- Đã hoàn thành việc tạo các Repository Interfaces cho module Exam:
  - IExamRepository: Interface định nghĩa các phương thức quản lý bài thi với các methods CRUD và filtering
  - IExamResultRepository: Interface định nghĩa các phương thức quản lý kết quả bài thi
  - IExamQuestionRepository: Interface định nghĩa các phương thức quản lý câu hỏi bài thi

### Triển khai Repository Interfaces
Các interfaces được thiết kế theo mẫu nhất quán, sử dụng kiểu `unknown` thay vì `any` để đảm bảo type safety. Ví dụ với IExamRepository:

```typescript
export interface IExamRepository {
  findAll(filters: ExamFilterDto): Promise<{ exams: unknown[]; total: number }>;
  findById(id: string): Promise<unknown | null>;
  findByCreator(creatorId: string): Promise<unknown[]>;
  findBySubject(subject: string): Promise<unknown[]>;
  findByGrade(grade: number): Promise<unknown[]>;
  create(data: unknown): Promise<unknown>;
  update(id: string, data: unknown): Promise<unknown>;
  delete(id: string): Promise<boolean>;
  updateAverageScore(id: string, score: number): Promise<unknown>;
}
```

### Bước tiếp theo
- Triển khai Exam API với ExamController, ExamService và ExamRepository
- Triển khai Question API
- Triển khai Attempt API (Làm bài thi)
- Triển khai Statistics API

## Tiến trình hiện tại

### Module Question
Đã hoàn thành:
- Thiết kế model Question trong schema.prisma với các trường:
  - Trường cơ bản: id, content, rawContent, type, createdAt, updatedAt
  - Trường đặc biệt: questionId, subcount, source, correctAnswer, status
  - Enum: QuestionType (MC, TF, SA, ES), QuestionStatus, QuestionImageType
  - Trường metadata: usageCount, creator, feedback
  - Mối quan hệ với các model khác: ExamQuestion, AssessmentQuestion, User (creator)
- Thiết kế model QuestionVersion lưu trữ lịch sử thay đổi
- Thiết kế model QuestionImage quản lý hình ảnh
- Thiết kế model QuestionTag phân loại câu hỏi
- Thiết kế model AssessmentQuestion để liên kết câu hỏi với Assessment
- Tất cả schema được xác thực (validated) thành công
- Tạo migration với Prisma (20250410164556_add_question_models)
- Apply migration vào database thành công

Cần làm tiếp:
- Tạo Prisma client types với prisma generate
- Triển khai Entity Classes trong packages/database/src/entities
- Triển khai DTO Classes
- Triển khai Repository Interfaces và implementation

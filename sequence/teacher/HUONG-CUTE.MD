## Use-case 1. Quản lý buổi học

- Sequence 1.1: Giảng viên thêm buổi học

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherLessonController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 1.1. Ấn nút  buổi học mới
    TeacherView-->>-Teacher: 1.2. Hiện modal yêu cầu nhập thông tin
    Teacher->>+TeacherView: 1.3. Điền thông tin buổi học mới
    Teacher->>+TeacherView: 1.4. Nhấn nút "Tạo buổi học"
    TeacherView->>+TeacherLessonController: 1.5.1. Gửi thông tin buổi học
    TeacherLessonController->>TeacherService: 1.5.2. CreateLesson()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 1.5.3. CreateLessonAsync()
        TeacherRepository->>+Database: 1.5.4. executeQuery()

        Database->>-TeacherLessonController: 1.5.5. return Lesson entity
        TeacherLessonController->>-TeacherView: 1.5.6. tạo buổi học thành công
    else invalid
        TeacherLessonController->>TeacherView: throw exception
    end
```

- Sequence 1.2: Giảng viên cập nhật buổi học

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherLessonController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 2.1. Ấn nút sửa nội dung
    TeacherView-->>-Teacher: 2.2. Chuyển đến trang sửa nội dung bài học
    Teacher->>+TeacherView: 2.3. Sửa nội dung bài học
    Teacher->>+TeacherView: 2.4. Nhấn nút "Lưu"
    TeacherView->>+TeacherLessonController: 2.5.1. Gửi id bài học
    TeacherLessonController->>TeacherService: 2.5.2. UpdateLesson()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 2.5.3. UpdateLessonByIdAsync()
        TeacherRepository->>+Database: 2.5.5. executeQuery()

        Database->>-TeacherLessonController: 2.5.5. return result
        TeacherLessonController->>-TeacherView: 2.5.6.1. cập nhật nội dung buổi học thành công
    else invalid
        TeacherLessonController->>TeacherView: 2.5.6.2.throw exception
    end
```

- Sequence 1.3: Giảng viên cập nhật nội dung buổi học

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherLessonController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 3.1. Ấn nút sửa nội dung
    TeacherView-->>-Teacher: 3.2. Chuyển đến trang sửa nội dung bài học
    Teacher->>+TeacherView: 3.3. Sửa nội dung bài học
    Teacher->>+TeacherView: 3.4. Nhấn nút "Lưu"
    TeacherView->>+TeacherLessonController: 3.5.1. Gửi id bài học
    TeacherLessonController->>TeacherService: 3.5.2. UpdateLessonContent()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 3.5.3. UpdateLessonContentByLessonIdAsync()
        TeacherRepository->>+Database: 3.5.5. executeQuery()

        Database->>-TeacherLessonController: 3.5.5. return result
        TeacherLessonController->>-TeacherView: 3.5.6.1. cập nhật nội dung buổi học thành công
    else invalid
        TeacherLessonController->>TeacherView: 3.5.6.2.throw exception
    end
```

- Sequence 1.4: Giảng viên xóa buổi học

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherLessonController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 4.1. Ấn nút xóa
    TeacherView-->>-Teacher: 4.2. Hiện thông báo xác nhận xóa
    Teacher->>+TeacherView: 4.3. Nhấn nút "Xóa"
    TeacherView->>+TeacherLessonController: 4.4.1. Gửi Id buổi học()
    TeacherLessonController->>TeacherService: 4.4.2. DeleteLesson()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 4.4.3. DeleteLessonByIdAsync()
        TeacherRepository->>+Database: 4.4.4. executeQuery()

        Database->>-TeacherLessonController: 4.4.5. return result
        TeacherLessonController->>-TeacherView: 4.4.6.1. xóa buổi học thành công
    else invalid
        TeacherLessonController->>TeacherView: 4.4.6.2.throw exception
    end
```

## Use-case 2. Quản lý bài kiểm tra của bài học

- sequence 2.1: Giảng viên thêm bài kiểm tra

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherTestController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 1.1. Ấn nút tạo bài kiểm tra mới
    TeacherView-->>-Teacher: 1.2. Hiện modal yêu cầu nhập thông tin
    Teacher->>+TeacherView: 1.3. Điền thông tin bài kiểm tra mới
    Teacher->>+TeacherView: 1.4. Nhấn nút "Tạo bài kiểm tra"
    TeacherView->>+TeacherTestController: 1.5.1. Gửi thông tin bài kiểm tra
    TeacherTestController->>TeacherService: 1.5.2. CreateTest()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 1.5.3. CreateTestAsync()
        TeacherRepository->>+Database: 1.5.4. executeQuery()

        Database->>-TeacherTestController: 1.5.5. return Test entity
        TeacherTestController->>-TeacherView: 1.5.6. tạo bài kiểm tra thành công
    else invalid
        TeacherTestController->>TeacherView: throw exception
    end
```

- sequence 2.2: Giảng viên cập nhật bài kiểm tra

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherTestController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 2.1. Ấn nút sửa bài kiểm tra
    TeacherView-->>-Teacher: 2.2. Chuyển đến trang sửa bài kiểm tra
    Teacher->>+TeacherView: 2.3. Sửa nội dung bài kiểm tra
    Teacher->>+TeacherView: 2.4. Nhấn nút "Lưu"
    TeacherView->>+TeacherTestController: 2.5.1. Gửi id bài kiểm tra
    TeacherTestController->>TeacherService: 2.5.2. UpdateTest()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 2.5.3. UpdateTestByIdAsync()
        TeacherRepository->>+Database: 2.5.4. executeQuery()

        Database->>-TeacherTestController: 2.5.5. return result
        TeacherTestController->>-TeacherView: 2.5.6.1. cập nhật nội dung bài kiểm tra thành công
    else invalid
        TeacherTestController->>TeacherView: 2.5.6.2.throw exception
    end
```

- sequence 2.3: Giảng viên xóa bài kiểm tra

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherTestController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 3.1. Ấn nút xóa
    TeacherView-->>-Teacher: 3.2. Hiện thông báo xác nhận xóa
    Teacher->>+TeacherView: 3.3. Nhấn nút "Xóa"
    TeacherView->>+TeacherTestController: 3.4.1. Gửi Id bài kiểm tra()
    TeacherTestController->>TeacherService: 3.4.2. DeleteTest()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 3.4.3. DeleteTestByIdAsync()
        TeacherRepository->>+Database: 3.4.4. executeQuery()

        Database->>-TeacherTestController: 3.4.5. return result
        TeacherTestController->>-TeacherView: 3.4.6.1. xóa bài kiểm tra thành công
    else invalid
        TeacherTestController->>TeacherView: 3.4.6.2.throw exception
    end
```

## Use-case 3. Quản lý câu hỏi của bài học

- sequence 3.1: Giảng viên thêm câu hỏi

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherQuestionController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 1.1. Ấn nút tạo câu hỏi mới
    TeacherView-->>-Teacher: 1.2. Hiện modal yêu cầu nhập thông tin
    Teacher->>+TeacherView: 1.3. Điền thông tin câu hỏi mới
    Teacher->>+TeacherView: 1.4. Nhấn nút "Tạo câu hỏi"
    TeacherView->>+TeacherQuestionController: 1.5.1. Gửi thông tin câu hỏi
    TeacherQuestionController->>TeacherService: 1.5.2. CreateQuestion()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 1.5.3. CreateQuestionAsync()
        TeacherRepository->>+Database: 1.5.4. executeQuery()

        Database->>-TeacherQuestionController: 1.5.5. return Question entity
        TeacherQuestionController->>-TeacherView: 1.5.6. Tạo câu hỏi thành công
    else invalid
        TeacherQuestionController->>TeacherView: throw exception
    end
```

- sequence 3.2: Giảng viên cập nhật câu hỏi

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherQuestionController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 2.1. Ấn nút sửa câu hỏi
    TeacherView-->>-Teacher: 2.2. Chuyển đến trang sửa câu hỏi
    Teacher->>+TeacherView: 2.3. Sửa nội dung câu hỏi
    Teacher->>+TeacherView: 2.4. Nhấn nút "Lưu"
    TeacherView->>+TeacherQuestionController: 2.5.1. Gửi id câu hỏi
    TeacherQuestionController->>TeacherService: 2.5.2. UpdateQuestion()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 2.5.3. UpdateQuestionByIdAsync()
        TeacherRepository->>+Database: 2.5.4. executeQuery()

        Database->>-TeacherQuestionController: 2.5.5. return result
        TeacherQuestionController->>-TeacherView: 2.5.6.1. Cập nhật nội dung câu hỏi thành công
    else invalid
        TeacherQuestionController->>TeacherView: 2.4.6.2.throw exception
    end
```

- sequence 3.3: Giảng viên xóa câu hỏi

```mermaid
sequenceDiagram
    participant Teacher
    participant TeacherView
    participant TeacherQuestionController
    participant TeacherService
    participant TeacherRepository
    participant Database

    Teacher->>+TeacherView: 3.1. Ấn nút xóa
    TeacherView-->>-Teacher: 3.2. Hiện thông báo xác nhận xóa
    Teacher->>+TeacherView: 3.3. Nhấn nút "Xóa"
    TeacherView->>+TeacherQuestionController: 3.4.1. Gửi Id câu hỏi
    TeacherQuestionController->>TeacherService: 3.4.2. DeleteQuestion()
    alt ServiceValidate()
        TeacherService->>+TeacherRepository: 3.4.3. DeleteQuestionByIdAsync()
        TeacherRepository->>+Database: 3.4.4. executeQuery()

        Database->>-TeacherQuestionController: 3.4.5. return result
        TeacherQuestionController->>-TeacherView: 3.4.6.1. Xóa câu hỏi thành công
    else invalid
        TeacherQuestionController->>TeacherView: 3.4.6.2.throw exception
    end
```

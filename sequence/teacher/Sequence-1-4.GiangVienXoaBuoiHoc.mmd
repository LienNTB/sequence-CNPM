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

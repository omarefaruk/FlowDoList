Flow Do List

A task management app for Android, built with Kotlin and Jetpack Compose using Clean Architecture, MVVM, Room and tests from the domain layer through to the UI.

Features
Create, edit and delete tasks with a title and description
Colour-code tasks
Sort tasks by date, title or colour, in ascending or descending order
Tasks are saved locally with Room, so they persist between sessions
Material 3 UI built entirely in Jetpack Compose
Architecture

The app follows Clean Architecture, organised by feature:

feature_task/
├── presentation/   Compose screens, ViewModels (MVVM), UI events and state
├── domain/         Use cases, Task model, repository interface, sorting logic
└── data/           Room database, DAO, repository implementation
MVVM: ViewModels hold screen state and handle UI events from Compose
Use cases: AddTask, DeleteTask, GetTask and GetTasks, grouped in TaskUseCases
Sorting: a sealed TaskOrder class (Title / Date / Colour) combined with OrderType (Ascending / Descending)
Repository pattern: the domain layer depends on an interface, so tests can use a fake repository
Dependency injection: Hilt, with a separate test module for instrumented tests
Tech stack

Kotlin · Jetpack Compose · Material 3 · Room · Coroutines & Flow · Hilt · Navigation Compose

Testing
Level	What's tested	Tools
Unit	GetTasks sorts correctly by title, date and colour in both directions (6 tests)	JUnit, fake repository
UI	Tasks screen behaviour	Compose UI testing, Hilt testing
End-to-end	Creating and viewing a task through the full app	Compose UI testing, Hilt test module
Running the project

Requirements: Android Studio (recent version), JDK 17, Android SDK API 24+

bash
git clone https://github.com/omarefaruk/FlowDoList.git

Open the project in Android Studio and run the app configuration.

bash
./gradlew test                  # unit tests
./gradlew connectedAndroidTest  # UI and end-to-end tests (needs an emulator or device)
What I'd add next
ViewModel unit tests
Room DAO tests against an in-memory database
Expose ViewModel state as StateFlow
Search and filtering
Contact

Omare Faruk · Android Developer · GitHub · LinkedIn

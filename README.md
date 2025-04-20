# Отчет по проекту "Система управления зоопарком"

## Реализованный функционал
1. **Добавление/удаление животного**  
   - Класс: `AnimalsController` (Presentation/Controllers/AnimalsController.cs)  
   - Методы: `AddAnimal` (POST /api/animals), `DeleteAnimal` (DELETE /api/animals/{id})

2. **Добавление/удаление вольера**  
   - Класс: `EnclosuresController` (Presentation/Controllers/EnclosuresController.cs)  
   - Методы: `AddEnclosure` (POST /api/enclosures), `DeleteEnclosure` (DELETE /api/enclosures/{id})

3. **Перемещение животного между вольерами**  
   - Класс: `AnimalTransferService` (Application/AnimalTransferService.cs)  
   - Контроллер: `AnimalsController` (метод `TransferAnimal`, POST /api/animals/{id}/transfer)

4. **Просмотр расписания кормления**  
   - Класс: `FeedingSchedulesController` (Presentation/Controllers/FeedingSchedulesController.cs)  
   - Метод: `GetSchedule` (GET /api/feedingschedules/{id})

5. **Добавление нового кормления**  
   - Класс: `FeedingOrganizationService` (Application/FeedingOrganizationService.cs)  
   - Контроллер: `FeedingSchedulesController` (метод `AddSchedule`, POST /api/feedingschedules)

6. **Статистика зоопарка**  
   - Класс: `ZooStatisticsService` (Application/ZooStatisticsService.cs)  
   - Методы: `GetTotalAnimals`, `GetFreeEnclosures`

## Примененные концепции

### Domain-Driven Design (DDD)
- **Богатая доменная модель**: Логика инкапсулирована в классах `Animal`, `Enclosure`, `FeedingSchedule` (Domain).
- **Value Objects**: Использованы перечисления `Gender`, `HealthStatus` (Domain).
- **Доменные события**: Реализован `AnimalMovedEvent` в `Animal.cs`.

### Clean Architecture
- **Слои**: 
  - Domain: Чистые модели (`Animal.cs`, `Enclosure.cs`).
  - Application: Сервисы и интерфейсы (`AnimalTransferService.cs`).
  - Infrastructure: Репозитории (`InMemoryAnimalRepository.cs`).
  - Presentation: Контроллеры (`AnimalsController.cs`).
- **Зависимости**: Domain не зависит от других слоев, Application зависит от Domain, Infrastructure и Presentation — от Application через интерфейсы.

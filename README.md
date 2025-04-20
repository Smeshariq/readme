# Отчет по мини-дз 2

## Реализованный функционал
1. **Добавление/удаление животного**  
   - Класс: `AnimalsController` 
   - Методы: `AddAnimal`, `DeleteAnimal`

2. **Добавление/удаление вольера**  
   - Класс: `EnclosuresController` 
   - Методы: `AddEnclosure`, `DeleteEnclosure`

3. **Перемещение животного между вольерами**  
   - Класс: `AnimalTransferService` 
   - Контроллер: `AnimalsController`

4. **Просмотр расписания кормления**  
   - Класс: `FeedingSchedulesController`
   - Метод: `GetSchedule`

5. **Добавление нового кормления**  
   - Класс: `FeedingOrganizationService`
   - Контроллер: `FeedingSchedulesController`

6. **Статистика зоопарка**  
   - Класс: `ZooStatisticsService`
   - Методы: `GetTotalAnimals`, `GetFreeEnclosures`

## Примененные концепции

### Domain-Driven Design
- **Доменная модель**: Логика инкапсулирована в классах `Animal`, `Enclosure`, `FeedingSchedule` (Domain).
- **Value Objects**: Использованы перечисления `Gender`, `HealthStatus` (Domain).
- **Доменные события**: Реализован `AnimalMovedEvent` в `Animal.cs`.

### Clean Architecture
- **Слои**: 
  - Domain: Чистые модели (`Animal.cs`, `Enclosure.cs`).
  - Application: Сервисы и интерфейсы (`AnimalTransferService.cs`).
  - Infrastructure: Репозитории (`InMemoryAnimalRepository.cs`).
  - Presentation: Контроллеры (`AnimalsController.cs`).
- **Зависимости**: Domain не зависит от других слоев, Application зависит от Domain, Infrastructure и Presentation — от Application через интерфейсы.

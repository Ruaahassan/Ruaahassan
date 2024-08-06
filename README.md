// Class Diagram for Breakdown Service System

// Class: Car
class Car {
    - model: String
    - year: int
    - registrationNumber: String
    + getCarInfo(): String
}

// Class: OnBoardSystem
class OnBoardSystem {
    - currentLocation: String
    + contactBreakdownService(service: BreakdownService, car: Car, numberOfPassengers: int): void
}

// Class: BreakdownService
class BreakdownService {
    + findNearestGarage(): void
    + findNearestHotel(): void
    + sendInfoToService(car: Car, numberOfPassengers: int): void
}

// Class: Garage
class Garage {
    - location: String
    + provideOffer(): Offer
}

// Class: Hotel
class Hotel {
    - location: String
    + provideOffer(): Offer
}

// Class: Offer
class Offer {
    - estimatedCost: double
    + getCost(): double
}

// Class: Client
class Client {
    - numberOfPassengers: int
    + requestService(system: OnBoardSystem, car: Car): void
}

// Relationships
Car "1" --> "1" OnBoardSystem : getCarInfo()
OnBoardSystem "1" --> "1" BreakdownService : contactBreakdownService()
BreakdownService "1" --> "1" Garage : findNearestGarage()
BreakdownService "1" --> "1" Hotel : findNearestHotel()
Garage "1" --> "1" Offer : provideOffer()
Hotel "1" --> "1" Offer : provideOffer()
Client "1" --> "1" OnBoardSystem : requestService()
BreakdownService "1" --> "1" Offer : getOffers()

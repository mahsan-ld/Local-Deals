@startuml

class Shopper {
  +id: UUID
  +name: String
  +email: String
  +location: String
  +preferences: List<String>
}

class Deal {
  +id: UUID
  +title: String
  +product: String
  +price: Float
  +savings: Float
  +validFrom: Date
  +validTo: Date
  +category: String
  +imageUrl: String
  +storeId: UUID
}

class Store {
  +id: UUID
  +name: String
  +address: String
  +hours: String
  +logoUrl: String
  +bannerUrl: String
  +ownerId: UUID
}

class Merchant {
  +id: UUID
  +name: String
  +email: String
  +role: String
  +storeId: UUID
}

class Engagement {
  +id: UUID
  +shopperId: UUID
  +dealId: UUID
  +action: String <<viewed/saved>>
  +timestamp: DateTime
}

class NotificationPreference {
  +id: UUID
  +shopperId: UUID
  +category: String
  +frequency: String
}

Shopper --> NotificationPreference
Shopper --> Engagement
Shopper --> Deal : "saves/views"
Deal --> Store
Store --> Merchant
Merchant --> Store : "manages"

@enduml

# E-Commerce Notification System
## Demonstrating SOLID Principles: ISP & DIP

A real-world example of Interface Segregation Principle (ISP) and Dependency Inversion Principle (DIP) in an e-commerce notification system.

## Project Structure
```
notification-system/
├── src/
│   ├── interfaces/           # ISP: Focused interfaces
│   │   ├── notification.ts
│   │   ├── formatters.ts
│   │   └── validators.ts
│   ├── implementations/      # Concrete implementations
│   │   ├── providers/
│   │   ├── formatters/
│   │   └── validators/
│   ├── services/            # DIP: High-level modules
│   │   └── notification-service.ts
│   ├── models/
│   │   └── notification-data.ts
│   └── index.ts
├── tests/
├── package.json
├── tsconfig.json
└── README.md
```

## Installation & Setup

```bash
npm install
npm run build
npm test
npm start
```

## Key SOLID Principles Demonstrated

### Interface Segregation Principle (ISP)
- ✅ Split large interfaces into focused, specific interfaces
- ✅ Clients depend only on interfaces they actually use
- ✅ No forced implementation of unused methods

### Dependency Inversion Principle (DIP)  
- ✅ High-level modules depend on abstractions (interfaces)
- ✅ Low-level modules implement abstractions
- ✅ Easy to swap implementations without changing business logic


// Run the demo
main().catch(console.error);
```
### tests/notification-service.test.ts
```typescript

## Usage Examples

### Basic Usage
```typescript
const service = new NotificationService(providers, formatters, validators);

await service.sendNotification({
  id: '123',
  recipient: 'user@example.com',
  subject: 'Welcome!',
  message: 'Thanks for joining us!',
  priority: 'high'
}, 'email');
```

### Adding New Providers (DIP)
```typescript
// Easy to add new providers without modifying existing code
class TeamsProvider implements NotificationProvider {
  // Implementation...
}

service.addProvider('teams', new TeamsProvider());
```

### ISP Benefits
- Email provider only implements interfaces it needs
- SMS provider doesn't need to implement email-specific methods  
- Push provider can implement bulk operations without tracking
- Clients depend only on interfaces they actually use

### DIP Benefits  
- High-level `NotificationService` depends on abstractions
- Easy to swap providers/formatters/validators
- Testable with mock implementations
- Flexible dependency injection
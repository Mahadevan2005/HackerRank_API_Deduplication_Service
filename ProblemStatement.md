# Java SpringBoot: Transaction Deduplication API

In this project, there is a transaction processing system where duplicate requests need to be identified and rejected within a time window. This is common in payment systems where network issues or retry logic can cause the same transaction to be submitted multiple times. The system uses a deduplication mechanism to ensure idempotency.

Here is an example of a transaction request JSON object:
```json
{
  "requestId": "TXN001",
  "amount": 100.00,
  "timestamp": 1700000000000
}
```

Here is an example of a transaction response JSON object:
```json
{
  "status": "SUCCESS",
  "message": "Transaction processed successfully",
  "transactionId": "550e8400-e29b-41d4-a716-446655440000"
}
```

The application should adhere to the following API format and response codes in `TransactionController`:

**POST /api/transactions**: 
- The request body will have a transaction instance with `requestId`, `amount`, and `timestamp`.
- If this is the first occurrence of the `requestId` within the last 5 minutes, process the transaction and return the response with `status: "SUCCESS"`, a generated `transactionId`, and status code **201**.
- If a transaction with the same `requestId` was already processed within the last 5 minutes, return a response with `status: "DUPLICATE"`, `transactionId: null`, and status code **200**.
- If the transaction fails validation (invalid `requestId`, negative `amount`, or invalid `timestamp`), return a response with `status: "FAILED"`, `transactionId: null`, and status code **400**.
- After 5 minutes have passed, a transaction with the same `requestId` should be treated as a new request.
- The implementation must handle concurrent requests safely.

**Implementation Requirements**:
- Complete the `processTransaction()` method in `TransactionService`.
- Use appropriate data structures for efficient duplicate detection.
- Ensure thread-safety for concurrent requests.
- Handle memory management appropriately to prevent unbounded 
growth of stored request records. (lazy cleanup during request processing or scheduled cleanup)
- Do not modify the provided `Transaction`, `TransactionResponse`, or `TransactionController` classes.

**Validation Rules**:
- `requestId`: Must not be null, empty, or whitespace-only
- `amount`: Must be positive (greater than 0)
- `timestamp`: Must not be null and should be within a reasonable range (not far future)

**Time Window**: 
- 5 minutes (300,000 milliseconds)
- If a second request with the same `requestId` is received **≤ 300,000 ms** after the first recorded request timestamp, it must be treated as **DUPLICATE**.
- If a second request is received **> 300,000 ms** after the first, it must be treated as a **new** request (i.e., processable again and should return SUCCESS when valid).
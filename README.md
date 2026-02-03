# nosql_template

## Run dev using docker
```
docker-compose up -d
```
**Frontend**
```
http://localhost:5173/
```
**Backend**
```
http://localhost:8000/
```
**Swagger UI**
```
http://localhost:8000/docs
```
## Default credentials

### Worker
- **email**: `worker@example.com`
- **password**:  `worker_123`

### Clients
1. - **email**: `client_1@example.com`
   - **password**:  `client_1`
2. - **email**: `client_2@example.com`
   - **password**:  `client_2`
3. - **email**: `client_3@example.com`
   - **password**:  `client_3`


## Run backend tests using docker
```sh
cd ./backend
```
```
docker-compose up -d
```
**Expected output** `======================= 154 passed, 45 warnings in 6.46s =======================`

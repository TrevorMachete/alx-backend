# 0x03. Queuing System in JS

## Tasks

### 0. Install a redis instance

### 1. Node Redis Client

- Install `node_redis` using npm
- Using Babel and ES6, write a script named `0-redis_client.js`. It should connect to the Redis server running on your machine:
  - It should log to the console the message `Redis client connected to the server` when the connection to Redis works correctly
  - It should log to the console the message `Redis client not connected to the server: ERROR_MESSAGE` when the connection to Redis does not work
- Requirements:
  - To import the library, you need to use the keyword `import`

### 2. Node Redis client and basic operations

- In a file `1-redis_op.js`, copy the code you previously wrote (`0-redis_client.js`).

### 3. Node Redis client and async operations

- In a file `2-redis_op_async.js`, let’s copy the code from the previous exercise (`1-redis_op.js`)
- Using `promisify`, modify the function `displaySchoolValue` to use ES6 `async` / `await`
- Same result as `1-redis_op.js`

### 4. Node Redis client and advanced operations

- In a file named `4-redis_advanced_op.js`, let’s use the client to store a hash value

### 5. Node Redis client publisher and subscriber

- In a file named `5-subscriber.js`, create a redis client

### 6. Create the Job creator

- In a file named `6-job_creator.js`:
  - Create a queue with Kue

### 7. Create the Job processor

- In a file named `6-job_processor.js`:
  - Create a queue with Kue
  - Create a function named `sendNotification`:
    - It will take two arguments `phoneNumber` and `message`
    - It will log to the console `Sending notification to PHONE_NUMBER, with message: MESSAGE`
  - Write the queue process that will listen to new jobs on `push_notification_code`:
    - Every new job should call the `sendNotification` function with the phone number and the message contained within the job data

### 8. Track progress and errors with Kue: Create the Job creator

- In a file named `7-job_creator.js`

### 9. Track progress and errors with Kue: Create the Job processor

- In a file named `7-job_processor.js`:
  - Create an array that will contain the blacklisted phone numbers. Add in it `4153518780` and `4153518781` - these 2 numbers will be blacklisted by our jobs processor.

### 10. Writing the job creation function

- In a file named `8-job.js`, create a function named `createPushNotificationsJobs`:
  - It takes into argument `jobs` (array of objects), and `queue` (Kue queue)
  - If `jobs` is not an array, it should throw an Error with message: `Jobs is not an array`
  - For each job in `jobs`, create a job in the queue `push_notification_code_3`
  - When a job is created, it should log to the console `Notification job created: JOB_ID`
  - When a job is complete, it should log to the console `Notification job JOB_ID completed`
  - When a job is failed, it should log to the console `Notification job JOB_ID failed: ERROR`
  - When a job is making progress, it should log to the console `Notification job JOB_ID PERCENT% complete`

### 11. Writing the test for job creation

- Now that you created a job creator, let’s add tests:
  - Import the function `createPushNotificationsJobs`
  - Create a queue with Kue
  - Write a test suite for the `createPushNotificationsJobs` function:
    - Use `queue.testMode` to validate which jobs are inside the queue
    - etc.

### 12. In stock?

- Data
  - Create an array `listProducts` containing the list of the following products:
    - Id: 1, name: Suitcase 250, price: 50, stock: 4
    - Id: 2, name: Suitcase 450, price: 100, stock: 10
    - Id: 3, name: Suitcase 650, price: 350, stock: 2
    - Id: 4, name: Suitcase 1050, price: 550, stock: 5

### 13. Can I have a seat?

- Redis
  - Create a Redic client:
    - Create a function `reserveSeat`, that will take into argument `number`, and set the key `available_seats` with the number
    - Create a function `getCurrentAvailableSeats`, it will return the current number of available seats (by using `promisify` for Redis)
    - When launching the application, set the number of available to 50
    - Initialize the boolean `reservationEnabled` to true - it will be turn to false when no seat will be available
- Kue queue
  - Create a Kue queue
- Server
  - Create an express server listening on the port 1245. (You will start it via: `npm run dev 100-seat.js`)
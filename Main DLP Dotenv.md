Файл .env — это конфигурация приложения, где задаются переменные окружения. Он 
позволяет хранить пароли, порты, ключи и настройки отдельно от кода, чтобы 
приложение легко запускалось в разных условиях: на ноутбуке разработчика, тестовом 
сервере или в продакшене.

```bash
# .env.example
# This is an example environment configuration file.
# Copy this file to .env and fill in the required values.

# Environment variables for the application
# Do not change the variable names, just fill in the values.
# Make sure to keep the quotes around the values if they contain special characters.
# Node.js environment
# NODE_ENV can be 'development', 'production', or 'test'
# It is recommended to set it to 'production' for production environments.
# For development, you can set it to 'development'.
# For testing, set it to 'test'.
NODE_ENV=production
# NODE_TLS_REJECT_UNAUTHORIZED is used to control whether Node.js should reject self-signed certificates.
# Set it to '0' to allow self-signed certificates, or '1' to reject them.
NODE_TLS_REJECT_UNAUTHORIZED="0"
# TZ (Time Zone) is used to set the time zone for the application.
# It is recommended to set it to your local time zone.
# For example, 'Asia/Tashkent' for Uzbekistan.
# You can find the list of time zones here: https://en.wikipedia.org/wiki/List_of_tz_database_time_zones
# Make sure to set it to the correct time zone for your
TZ=Asia/Tashkent

# JWT (JSON Web Token) settings
# JWT is used for authentication and authorization.
# It should be a long, secure secret key.
# Make sure to change it to a secure value in production.
# JWT_EXPIRES_IN_MINUTE defines how long the JWT token is valid.
# It can be set to a duration like '30m' for 30 minutes.
JWT="SUp3rS3cur3&L0ng-Secret-K3y!"
JWT_EXPIRES_IN_MINUTE=30m

# MongoDB settings
# MONGO_HOSTNAME is the hostname of the MongoDB server.
MONGO_HOSTNAME=localhost
# MONGO_PORT is the port on which MongoDB is running.
MONGO_PORT=27017
# MONGO_DB is the name of the MongoDB database to use.
MONGO_DB=demo,
# MONGO_LOGIN and MONGO_PASSWORD are optional credentials for MongoDB authentication.
# If your MongoDB server does not require authentication, you can leave these empty.
MONGO_LOGIN=
MONGO_PASSWORD=

# Redis settings
# REDIS_HOST is the hostname of the Redis server.
# REDIS_PORT is the port on which Redis is running.
# Redis is used for caching and session management.
REDIS_HOST=localhost
REDIS_PORT=6379

# SERVICES SETTINGS BEGIN
DATA_PATH='/var/lib/datagaze'
CONFIG_PATH='/etc/datagaze'

# Log
# LOG_OUTPUT_MODE console is written to the console
# LOG_OUTPUT_MODE file is written to a file
# LOG_OUTPUT_MODE both is written to both console and file
LOG_OUTPUT_MODE=console # console | file | both
# LOG_LEVEL controls the logging level
# Available levels: error, warn, info, http, debug
# In production, it is recommended to set it to 'info' or 'error'
# In development, you can set it to 'debug' for more detailed logs
# If you want to log HTTP requests, set it to 'http'
# If you set it to 'warn', it will log warnings and errors
# If you set it to 'error', it will log only errors
# If you set it to 'debug', it will log everything including debug information
# Default is 'info' is recommended for production
LOG_LEVEL=info # error | warn | info | http | debug

# Server service settings
# SERVER_PORT is the port on which the server will listen for incoming requests.
# SERVER_INTERNAL_HTTPS_PORT is the port for internal HTTPS communication.
# SERVER_SWAGGER_HOST is the hostname and pport of the server and will be use when swagger is enabled.
SERVER_PORT=3500
#MAX_OLD_SPACE_SIZE - node process heap limit
# default value 512 MB for x86, and 2048 MB for x64
SERVER_MAX_OLD_SPACE=2048
SERVER_INTERNAL_HTTPS_PORT=4443
# Server hhttp redirect to https enabled
# If set to true, the server will redirect HTTP requests to HTTPS.
# default is true.
SERVER_HTTP_REDIRECT_TO_HTTPS_ENABLED=true
# SERVER_SWAGGER_HOST is used to try it out on Swagger documentation.
SERVER_SWAGGER_ENABLED=false
SERVER_SWAGGER_HOST=localhost:3500
SERVER_SWAGGER_BASIC_AUTH_USERNAME='dev'
SERVER_SWAGGER_BASIC_AUTH_PASSWORD='123'
# SERVER_METRICS_ENABLED is used to enable or disable the server metrics.
# If set to true, the server will expose metrics for monitoring.
# These metrics can be used with monitoring tools like Prometheus.
APP_SERVER_METRICS_ENABLED=true
SERVER_PORT_METRICS=9510
SERVER_LOG_ENABLED=false
# Server caching settings, redis caching, expiration time in seconds
CACHING_TTL=86400 # 24 hours in seconds
CLEANING_INTERVAL_DAYS=10
REPORT_PERIOD_MAX_DAYS=93
# LOGGING SETTINGS
# If you want to enable logging, set it to true and it will be write to channel collection extractedText field with content.
# Example:
# extractedText = {
#        from: textExtractMethod.OCR,
#        content: contentToSave,
#        wasCropped
#    }
SAVE_EXTRACTED_TEXT_TO_LOG=true


# Agent service settings
# AGENT_PORT is the port on which the agent will listen for incoming requests.
AGENT_PORT=3501
# AGENT_SWAGGER_ENABLED is used to enable or disable the Swagger UI for the agent.
AGENT_SWAGGER_ENABLED=false
# AGENT_SWAGGER_BASIC_AUTH_USERNAME and AGENT_SWAGGER_BASIC_AUTH_PASSWORD are used for 
basic authentication on the agents Swagger UI.
# Make sure to set these to secure values
AGENT_SWAGGER_BASIC_AUTH_USERNAME='devDLP'
AGENT_SWAGGER_BASIC_AUTH_PASSWORD='Ge+%A5/_!$cjTu?ef'
#MAX_OLD_SPACE_SIZE - node process heap limit
# default value 512 MB for x86, and 2048 MB for x64
AGENT_MAX_OLD_SPACE=2048
APP_AGENT_METRICS_ENABLED=true
AGENT_PORT_METRICS=9501
AGENT_LOG_ENABLED=false
MIN_DISK_SPACE_PERCENTAGE=10

# RDV (Remote Data View) service settings
# RDV_HOST is the hostname on which the RDV service will listen.
# RDV_PORT is the port on which the RDV service will listen for incoming requests.
RDV_HOST=0.0.0.0
RDV_PORT=3502
APP_RDV_METRICS_ENABLED=true
RDV_PORT_METRICS=9512
RDV_LOG_ENABLED=true
#MAX_OLD_SPACE_SIZE - node process heap limit
# default value 512 MB for x86, and 2048 MB for x64
RDV_MAX_OLD_SPACE=2048

# Socket service settings
SOCKET_PORT=3503
#MAX_OLD_SPACE_SIZE - node process heap limit
# default value 512 MB for x86, and 2048 MB for x64
SOCKET_MAX_OLD_SPACE=2048
APP_SOCKET_METRICS_ENABLED=true
SOCKET_PORT_METRICS=9513
SOCKET_LOG_ENABLED=true

# Healthcheck service settings
HEALTHCHECK_PORT=3504
#MAX_OLD_SPACE_SIZE - node process heap limit
# default value 512 MB for x86, and 2048 MB for x64
HEALTHCHECK_MAX_OLD_SPACE=2048
APP_HEALTHCHECK_METRICS_ENABLED=true
HEALTHCHECK_LOG_ENABLED=false

# OCR service settings
# OCR_VERSION: 1 || 2
OCR_ENABLED=false
OCR_VERSION=2
OCR_SERVER=localhost
OCR_SERVER_PORT=8282
OCR_TOKEN='asdjkhj8hsd!s8adhASas'
OCR_SHARED_FOLDER='/'
OCR_REAL_TIME_FILE_SIZE_LIMIT=52428800 # 50 MB
#OCR response log
OCR_EXTRACT_RESPONSE_ENABLED=false
#OCR RABBITMQ SERVER
RABBIT_HOST=localhost
RABBIT_PORT=5672
RABBIT_USER=admin
RABBIT_PASSWORD=admin
RABBIT_EXCHANGE='results'
RABBIT_QUEUE='ocr_results'
#OCR SERVICE PARAMS END

#UEBA service settings
UEBA_ENABLED=true
UEBA_HOST=localhost
UEBA_PORT=3505
UEBA_SWAGGER_ENABLED='disabled'
UEBA_SWAGGER_PASS="123"
UEBA_MONGO_MAX_POOL_SIZE=100
UEBA_BAUTH_USERNAME=uebauserdev
UEBA_BAUTH_PASSWORD="123"
UEBA_LOG_ENABLED=false
#MAX_OLD_SPACE_SIZE - node process heap limit
# default value 512 MB for x86, and 2048 MB for x64
UEBA_EXPORTER_MAX_OLD_SPACE=2048
#IF UEBA_MAX_LIMIT_* undefined then will be use it
UEBA_MAX_LIMIT=20
#IF UEBA_MAX_DAYS_* undefined then will be use it
UEBA_MAX_DAYS=10
UEBA_MAX_LIMIT_APP_ACTIVITY=20
UEBA_MAX_DAYS_APP_ACTIVITY=10
UEBA_MAX_LIMIT_DEVICE_USAGE=20
UEBA_MAX_DAYS_DEVICE_USAGE=10
UEBA_MAX_LIMIT_EMAIL_ACTIVITY=20
UEBA_MAX_DAYS_EMAIL_ACTIVITY=10
UEBA_MAX_LIMIT_FILE_OPERATION=20
UEBA_MAX_DAYS_FILE_OPERATION=10
UEBA_MAX_LIMIT_NA_FILE_SNIFFS=20
UEBA_MAX_DAYS_NA_FILE_SNIFSS=10
UEBA_MAX_LIMIT_NA_RDPS=20
UEBA_MAX_DAYS_NA_RDPS=10
UEBA_MAX_LIMIT_NA_WEB_VISITING=20
UEBA_MAX_DAYS_NA_WEB_VISITING=10
UEBA_MAX_LIMIT_USERS=20
# Anomaly detector service params
UEBA_ANOMALY_DB_NAME=uebadb
UEBA_ANOMALY_DB_HOST=192.168.100.17
UEBA_ANOMALY_DB_PORT=5432
UEBA_ANOMALY_DB_USER=postgres
UEBA_ANOMALY_DB_PASSWORD=1upedbga2

# Worker service settings
# ANALYZE SMALL FILE SETTINGS
# used to separate analyze process small files from big files
# If file size less than ANALYZE_SMALL_FILE_MAX_SIZE, then it will be analyzed on the one queue else it will be analyzed on the another queue
ANALYZE_SMALL_FILE_MAX_SIZE=52428800
#MAX_OLD_SPACE_SIZE - node process heap limit
# default value 512 MB for x86, and 2048 MB for x64
WORKER_MAX_OLD_SPACE=2048
WORKER_LOG_ENABLED=true
#Больше всего использует агент воркер
APP_AGENT_CLUSTER_WORKERS=1
# Выдовать половину CPU
APP_SOCKET_CLUSTER_WORKERS=1
APP_WORKER_CLUSTER_WORKERS=1

#BACKUP#
BACKUP_DIR="../backup"
BACKUP_BMQ_LOCK_DURATION=30000
BACKUP_BMQ_TIMEOUT=30000

# Test manager settings
# If you want to use test manager, set TEST_MANAGER_ENABLED to true
# and provide the TEST_MANAGER_URI and TEST_MANAGER_REQUEST_ID_BOUNDARY_SYMBOL.
# If you don't want to use test manager, set TEST_MANAGER_ENABLED to false
# and leave the other variables as they are.
TEST_MANAGER_ENABLED=false
TEST_MANAGER_URI=http://localhost:8082/response
# it symboll will be used to separate test manager sent id from other texts
TEST_MANAGER_REQUEST_ID_BOUNDARY_SYMBOL="!#!"
```

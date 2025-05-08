# Используем lightweight образ с Java 17
FROM eclipse-temurin:17-jdk-alpine

# Устанавливаем необходимые утилиты
RUN apk add --no-cache \
    curl \
    busybox-extras  # Для ping, nslookup и др.

# Создаем директорию приложения
WORKDIR /app

# Копируем собранный JAR (имя должно совпадать с вашим артефактом)
COPY target/discovery-service1-*.jar app.jar

# Открываем порт Eureka
EXPOSE 8761

# Устанавливаем переменные JVM по умолчанию
ENV JAVA_TOOL_OPTIONS="-Dsun.net.inetaddr.ttl=0 -Dsun.net.inetaddr.negative.ttl=0"

# Используем ENTRYPOINT через sh -c для поддержки переменных окружения
ENTRYPOINT ["sh", "-c", "java $JAVA_TOOL_OPTIONS -jar app.jar"]

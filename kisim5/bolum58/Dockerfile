FROM mcr.microsoft.com/java/jdk:8-zulu-alpine AS compiler
COPY /source /usr/src/uygulama
WORKDIR /usr/src/uygulama
RUN javac uygulama.java

FROM mcr.microsoft.com/java/jre:8-zulu-alpine
WORKDIR /uygulama
COPY --from=compiler /usr/src/uygulama .
CMD [ "java", "uygulama" ]

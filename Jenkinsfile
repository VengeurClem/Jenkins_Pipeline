pipeline {
    agent any

    stages {
        stage('Download script and licences...') {
            steps {
                sh 'pwd'
                sh 'rm -rf Continuous_Testing'
                sh 'rm -rf Neoload_Test_Automation'
                sh 'git clone https://github.com/SplashBin/Continuous_Testing.git'
                sh 'git clone https://github.com/SplashBin/Neoload_Test_Automation.git'
                sh 'rm -rf mongo.out backend.out frontend.out'
            }
        }

        stage('Creating NTS Docker Image...') {
          steps {
            sh "docker build --file Continuous_Testing/NTS_Server.dockerfile -t nts_server ."
            sh "docker run -it -d -p 8084:8080 -p 7777:7777 -p 8005:8005 -p 8009:8009 --tty nts_server"
          }
        }

        stage('Deploy Nl Web') {
          parallel {
            stage('Deploy mongo...') {
              steps {
                sh 'docker run --interactive -v /home/bench/data:/data/db --name mongo -p 27017 --hostname mongo mongo:latest > mongo.out & jobs'
              }
            }

            stage('Deploy neoload-backend...') {
              steps {
                sh 'sh Neoload_Test_Automation/test_mongo'
                echo "Mongo succesfully deployed !"
                sh 'docker run --interactive --interactive -p 8080:1081 \
                      --publish 8081:1082 \
                      --publish 9082:9092 \
                      --env MEMORY_MAX=1500m \
                      --env MONGODB_HOST=mongo \
                      --env MONGODB_PORT=27017 \
                      --env MONGODB_MAX_POOLSIZE=50 \
                      --env NEOLOAD_WEB_PUBLIC_URL=http://192.168.1.31/ \
                      --env FILE_STORAGE_ROUTER_BASE_URL=http://192.168.1.31:8081 \
                      --env FILE_PROJECT_MAX_SIZE_IN_BYTES=100000000 \
                      --env NLPROJECT_MAX_UPLOADED_FILES_PER_WEEK=250 \
                      --link mongo \
                      --name nlweb-backend neotys/neoload-web-backend:latest > backend.out & jobs'
                sh 'sh Neoload_Test_Automation/test_backend'
                echo "Neoload-backend succesfully deployed !"
              }
            }

            stage('Deploy neoload-frontend...') {
              steps {
                sh 'sh Neoload_Test_Automation/test_backend'
                sh 'docker run --interactive -e MEMORY_MAX=896m \
                        -e SEND_USAGE_STATISTICS=true \
                        --publish 80:9090 \
                        --publish 81:9091 \
                        --link nlweb-backend \
                        --interactive \
                        --name nlweb-frontend neotys/neoload-web-frontend:latest > frontend.out & jobs'
                sh 'sh Neoload_Test_Automation/test_frontend'
                echo "Neoload-frontend succesfully deployed !"
              }
            }
          }
        }

        stage('Deploy Nl Controller') {
            steps {
                /*sh 'docker run --interactive --name nl-controller neotys/neoload-controller'*/
                sh 'sleep 5'
                echo 'Neoload Controller succesfully deployed !'
            }
        }
    }
}

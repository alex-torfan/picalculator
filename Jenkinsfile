node {
    stage("scm") {
        git url: 'https://github.com/alex-torfan/picalculator'
    }
    stage("test and build") {
        sh "docker build -t alexei87/picalculator ."
    }
    stage("push") {
        withCredentials([[
            $class: 'UsernamePasswordMultiBinding', 
             credentialsId: 'docker_hub',
             usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD'
        ]]) {
            sh "docker login -u $USERNAME -p $PASSWORD"
            sh "docker push alexei87/picalculator"
        }
    }
}
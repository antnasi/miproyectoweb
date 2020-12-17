pipeline{
    
  agent any
  stages{
      
    stage('Etapa1'){
        
        steps{
            echo'soy el primer paso de la etapa1'
            git url:'https://github.com/antnasi/miproyectoweb'
        }
    }  
    stage('Etapa2'){
        
        steps{
            echo'empaqueto el proyecto'
            sh 'mvn package'
        }
    }  
    
    stage('Etapa3'){
        
        steps{
            echo'despliegue en tomcat'
            sh deploy adapters: [tomcat9(credentialsId: '1181adc2-7a31-4562-b817-f2e21ef201d2', path: '', url: 'http://localhost:8082')], contextPath: 'prueba', war: 'target/miproyectoweb.war'
        }
    }  
  }
  post{
      
      always{
          echo'Yo me ejecuto siempre'
      }
      success{
          echo'Yo me ejecuto cuando todo ha ido bien'
      }
      failure{
          echo'Yo me ejecuto cuando todo ha ido mal'
      }
      changed{
        echo'Yo me ejecuto si la ejecución termina como la anterior'
      }
  }  
}
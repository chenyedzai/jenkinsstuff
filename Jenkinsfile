pipeline {

    agent any
    parameters{
        //path: the path of where the files are
        string(name: 'DIR1', defaultValue: 'path/*', description: 'Vars dir')
        string(name: 'DIR2', defaultValue: 'path/*', description: 'Vars dir')
        booleanParam(name: 'CHECK_BOX',defaultValue: false,description: 'checkbox')
    } 
    stages {  
        stage('options'){
           steps {
               script {
                  env.OPTION = input message: 'Choose stack', ok: 'next',
                      parameters: [choice(name: "OPTION", choices: "example1\nexample2", description: "example")]
                    
               }
               echo "${env.OPTION}"           
           }            
        }          
        stage('Read filenames from directory'){
           steps {
               
               script {
                   def option = []
                   def vars = []
                   if (env.OPTION=='example1'){
                   def files = findFiles(glob: "${DIR1}")
                //   echo files[0].name
                   for (i = 0; i <files.size(); i++) {
                    echo files[i].name
                //removing extensions
                    option << files[i].name.take(files[i].name.lastIndexOf('.'))
                    vars << files[i].name    
                   }
                   println option
                                        
                  env.FILE = input message: 'Choose option', ok: 'next',
                      parameters: [choice(name: "FILE", choices: option, description: "Stack")]
                   }
                   else{
                       echo "${env.FILE}"
                   }
                    
               }
               
           }            
        }  
        
    }
    }
cd <project-folder>
git init
git add .
git commit -m "Initial Commit"
git remote add origin https://github.com/<username>/<repo>.git
git remote -v
git branch -M main
git push -u origin main
------------------------------------
if test file causes any error 
delete the test file from project in eclipse
git add .
git commit -m "Removed AppTest"
git pull origin main --allow-unrelated-histories
git push origin main
------------------------------------------------
pipeline { 
    agent any 
 
    tools { 
        maven 'Maven' 
        jdk 'JDK' 
    } 
 
    stages { 
 
        stage('Checkout') { 
            steps { 
                git branch: 'main', 
                url: URL 
            } 
        } 
 
        stage('Build') { 
            steps { 
                bat 'mvn clean package' 
            } 
        } 
    } 
} 

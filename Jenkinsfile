node("docker") {
    docker.withRegistry('https://cloud.docker.com/repository/registry-1.docker.io/sacdes/poc-tcs', 'DOCKERHUB') {
    
        git url: "https://github.com/SACDES7204/poc-tcs.git/", credentialsId: 'GITHUB'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "poc-tcs"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}

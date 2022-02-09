node {
def to = emailextrecipients([
           "nreddynaveen2@gmail.com",
])

try {
 stage{'build') {
  println(" so far so good")
  }
  stage('test') {
  println(" A test has failed")
  sh 'exit 1'
  }
}
catch(e) {
result = "Failure";
def subject = "${env.JOB_NAME} - Build #${env.BUILD_NUMBER} ${result}"

def content = '${JELLY_SCRIPT,template="html"}'

if(to != null && !to.isEmpty()) {
      emailext(body: content, mimeType: 'text/html',
         subject: subject,
         to: to, attachLog: true )
}

throw e;
}
}

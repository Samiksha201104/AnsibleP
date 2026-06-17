pipeline{
agent any
tools{
maven 'Maven'
}
environmtnt{
LANG=en_US.UTF-8
LC=en_US.UTF-8
}
stages
{
stage('Checkout')
{
steps{
git branch:'master',url:'https://github.com/Samiksha201104/AnsibleP.git'
}}
stage('Build')
{
steps{
sh 'mvn clean package'
}}
stage('archive')
{
steps{
archiveArtifacts artifacts:'target/*.war',fingerprint:true
}}
stage('Deploy')
{
steps
{
sh 'mvn clean package'
sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
}}}
post{
success{
echo 'Build success'
}
failure{
echo 'Build fail'
}
}
}

// Powered by Infostretch 

timestamps {

node () {

	stage ('Build - Checkout') {
 	 checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'pumej-gitpasswd', url: 'https://github.com/Mexxy-lab/CICD-project-javaapp.git']]]) 
	}
	stage ('Build - Build') {
 			// Maven build step
	withMaven(maven: 'Maven-3.9.10', mavenSettingsFilePath: 'settings.xml') { 
 			if(isUnix()) {
 				sh "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 install -DskipUnitTests " 
			} else { 
 				bat "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 install -DskipUnitTests " 
			} 
 		}
		archiveArtifacts allowEmptyArchive: false, artifacts: '**/*.war', caseSensitive: true, defaultExcludes: true, fingerprint: false, onlyIfSuccessful: false 
	}
	stage ('Test - Build') {
 			// Maven build step
	withMaven(maven: 'Maven-3.9.10', mavenSettingsFilePath: 'settings.xml') { 
 			if(isUnix()) {
 				sh "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 test " 
			} else { 
 				bat "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 test " 
			} 
 		} 
	}
	stage ('Integration Test - Build') {
 			// Maven build step
	withMaven(maven: 'Maven-3.9.10', mavenSettingsFilePath: 'settings.xml') { 
 			if(isUnix()) {
 				sh "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 verify -DskipUnitTests " 
			} else { 
 				bat "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 verify -DskipUnitTests " 
			} 
 		} 
	}
	stage ('Code Analysis - Build') {
 			// Maven build step
	withMaven(maven: 'Maven-3.9.10', mavenSettingsFilePath: 'settings.xml') { 
 			if(isUnix()) {
 				sh "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 checkstyle:checkstyle " 
			} else { 
 				bat "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 checkstyle:checkstyle " 
			} 
 		} 
	}
	stage ('SonarScanner-CodeAnalysis - Build') {
 	
withEnv(["JAVA_HOME=${ tool '"+JDK+"' }", "PATH=${env.JAVA_HOME}/bin"]) { 
		// Maven build step
	withMaven(jdk: 'java17', maven: 'Maven-3.9.10', mavenSettingsFilePath: 'settings.xml') { 
 			if(isUnix()) {
 				sh "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 install " 
			} else { 
 				bat "mvn -DSNAP-REPO=vprofile-snapshot -DNEXUS-USER=admin -DNEXUS-PASS=admin123 -DRELEASE-REPO=vprofile-release -DCENTRAL-REPO=vpro-maven-central -DNEXUS-GRP-REPO=vpro-maven-group -DNEXUSIP=192.168.248.134 -DNEXUSPORT=8081 install " 
			} 
 		}
// Unable to convert a build step referring to "hudson.plugins.sonar.SonarRunnerBuilder". Please verify and convert manually if required. 
	}
}
	stage ('DeployNexus - Build') {
 	
// Unable to convert a build step referring to "hudson.plugins.copyartifact.CopyArtifact". Please verify and convert manually if required.
// Unable to convert a build step referring to "sp.sd.nexusartifactuploader.NexusArtifactUploader". Please verify and convert manually if required. 
	}
}
}
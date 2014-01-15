# Easier this way to get the desired build options
%define fedora 20
%{?_javapackages_macros:%_javapackages_macros}
%global namedreltag .RELEASE
%global namedversion %{version}%{?namedreltag}
Name:          springframework
Version:       3.1.4
Release:       2.0%{?dist}
Summary:       Spring Java Application Framework
Epoch:         0
License:       ASL 2.0
URL:           http://www.springframework.org
# Latest release require asm4 and cglib3
Source0:       https://github.com/spring-projects/spring-framework/archive/v%{namedversion}.tar.gz
Source1:       %{name}-3.1.4.RELEASE-pom.xml

# Use the JCA API provided by JBoss:
Patch0:        %{name}-use-jboss-jca-api.patch
# Use the correct Derby artifact id:
Patch1:        %{name}-fix-derby-aid.patch
# Change: com.springsource.commonj with geronimo-commonj_1.1_spec
#         opensymphony with org.quartz-scheduler
# Remove: javax.activation
# Fix jasperreports gId
Patch2:        %{name}-3.1.1-context_support-pom.patch
# Fix build with velocity 1.7
Patch3:        %{name}-3.1.1-velocity.patch
# Use jboss-connector-api_1.6_spec instead of geronimo-j2ee-connector_1.5_spec
Patch4:        %{name}-3.1.1-jms-connector-api.patch
# Fix openjpa deps
# Remove: ibatis-sqlmap (see http://attic.apache.org/projects/ibatis.html)
#         org.eclipse.persistence.jpa (part of eclipselink core)
#         org.eclipse.persistence.asm (eclipselink use system asm3)
#         org.eclipse.persistence.antlr (eclipselink use system antlr2)
#         hibernate-cglib-repack (unavailable use cglib)
#         hibernate-annotations (part of hibernate-core)
# Fix cglib aId
Patch5:        %{name}-3.1.4-orm-pom.patch
# Add jpa-2.0-api support
Patch6:        %{name}-3.1.1-orm-jpa_api.patch
# Add tiles-el
Patch7:        %{name}-3.1.1-web_servlet-pom.patch
# Fix struts deps
Patch8:        %{name}-3.1.1-struts-pom.patch
# Build with Quartz 2.x only
Patch9:        %{name}-3.1.1-no-quartz1.patch
# Add missing servlet 3.0 methods
Patch10:       %{name}-3.1.4-test-servlet30.patch
# Add OSGi MANIFESTs
Patch11:       %{name}-3.1.4-osgi-support.patch
# Don't rename the asm package:
Patch12:       %{name}-3.1.4-dont-rebundle-asm.patch
# Replace all alias with proper aId:aId:version
# e.g. org.springframework.context use geronimo-ejb_3.0_spec
#      org.springframework.transaction use com.springsource.javax.ejb
#      now use geronimo-ejb_3.1_spec
Patch13:       %{name}-3.1.4-fix-javax-apis.patch
# Remove some code which don't compile with Hibernate Validator 5.x
Patch14:       %{name}-3.1.4-hibernate-validator5.patch

BuildRequires: hibernate3
BuildRequires: hibernate3-entitymanager
BuildRequires: mvn(aopalliance:aopalliance)
BuildRequires: mvn(asm:asm)
BuildRequires: mvn(asm:asm-commons)
BuildRequires: mvn(axis:axis)
BuildRequires: mvn(cglib:cglib)
BuildRequires: mvn(com.caucho:hessian)
BuildRequires: mvn(com.fasterxml:oss-parent)
BuildRequires: mvn(com.fasterxml.jackson.core:jackson-databind)
BuildRequires: mvn(com.h2database:h2)
BuildRequires: mvn(com.jamonapi:jamon)
BuildRequires: mvn(com.lowagie:itext)
BuildRequires: mvn(com.mchange:c3p0)
BuildRequires: mvn(com.sun.xml.bind:jaxb-impl)
BuildRequires: mvn(com.thoughtworks.xstream:xstream)
BuildRequires: mvn(commons-beanutils:commons-beanutils)
BuildRequires: mvn(commons-collections:commons-collections)
BuildRequires: mvn(commons-fileupload:commons-fileupload)
BuildRequires: mvn(commons-httpclient:commons-httpclient)
BuildRequires: mvn(commons-lang:commons-lang)
BuildRequires: mvn(commons-logging:commons-logging)
BuildRequires: mvn(commons-pool:commons-pool)
BuildRequires: mvn(javax.inject:javax.inject)
BuildRequires: mvn(javax.jdo:jdo2-api)
BuildRequires: mvn(javax.mail:mail)
BuildRequires: mvn(javax.portlet:portlet-api)
BuildRequires: mvn(joda-time:joda-time)
BuildRequires: mvn(junit:junit)
BuildRequires: mvn(log4j:log4j)
BuildRequires: mvn(net.sf.ehcache:ehcache-core)
BuildRequires: mvn(net.sf.jasperreports:jasperreports)
%if 0
# see https://bugzilla.redhat.com/show_bug.cgi?id=1005503
BuildRequires: mvn(net.sf.jopt-simple:jopt-simple)
%endif
BuildRequires: mvn(net.sourceforge.jexcelapi:jxl)
BuildRequires: mvn(org.apache.derby:derby)
BuildRequires: mvn(org.apache.derby:derbyclient)
BuildRequires: mvn(org.apache.geronimo.specs:specs)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-annotation_1.1_spec)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-commonj_1.1_spec)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-ejb_3.1_spec)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-interceptor_3.0_spec)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-jaxrpc_1.1_spec)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-jms_1.1_spec)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-jta_1.1_spec)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-saaj_1.3_spec)
BuildRequires: mvn(org.apache.geronimo.specs:geronimo-validation_1.0_spec)
BuildRequires: mvn(org.apache.httpcomponents:httpclient)
BuildRequires: mvn(org.apache.openjpa:openjpa-jdbc)
BuildRequires: mvn(org.apache.openjpa:openjpa-jest)
BuildRequires: mvn(org.apache.openjpa:openjpa-kernel)
BuildRequires: mvn(org.apache.openjpa:openjpa-lib)
BuildRequires: mvn(org.apache.openjpa:openjpa-persistence)
BuildRequires: mvn(org.apache.openjpa:openjpa-persistence-jdbc)
BuildRequires: mvn(org.apache.openjpa:openjpa-slice)
BuildRequires: mvn(org.apache.openjpa:openjpa-xmlstore)
BuildRequires: mvn(org.apache.poi:poi)
BuildRequires: mvn(org.apache.struts:struts-core)
BuildRequires: mvn(org.apache.struts:struts-extras)
BuildRequires: mvn(org.apache.struts:struts-tiles)
BuildRequires: mvn(org.apache.tiles:tiles-api)
BuildRequires: mvn(org.apache.tiles:tiles-core)
BuildRequires: mvn(org.apache.tiles:tiles-el)
BuildRequires: mvn(org.apache.tiles:tiles-jsp)
BuildRequires: mvn(org.apache.tiles:tiles-servlet)
BuildRequires: mvn(org.apache.tomcat:tomcat-catalina)
BuildRequires: mvn(org.apache.tomcat:tomcat-el-api)
BuildRequires: mvn(org.apache.tomcat:tomcat-jsp-api)
BuildRequires: mvn(org.apache.tomcat:tomcat-servlet-api)
BuildRequires: mvn(org.apache.xmlbeans:xmlbeans)
BuildRequires: mvn(org.aspectj:aspectjweaver)
BuildRequires: mvn(org.beanshell:bsh)
BuildRequires: mvn(org.codehaus.castor:castor-xml)
BuildRequires: mvn(org.codehaus.groovy:groovy)
BuildRequires: mvn(org.codehaus.jackson:jackson-mapper-asl)
BuildRequires: mvn(org.eclipse.persistence:org.eclipse.persistence.core)
BuildRequires: mvn(org.freemarker:freemarker)
BuildRequires: mvn(org.hamcrest:hamcrest-all)
BuildRequires: mvn(org.hibernate:hibernate-validator)
BuildRequires: mvn(org.hibernate.javax.persistence:hibernate-jpa-2.0-api)
BuildRequires: mvn(org.jboss.spec.javax.resource:jboss-connector-api_1.6_spec)
BuildRequires: mvn(org.jboss.spec.javax.faces:jboss-jsf-api_2.1_spec)
BuildRequires: mvn(org.jibx:jibx-run)
BuildRequires: mvn(org.jruby.extras:bytelist)
BuildRequires: mvn(org.quartz-scheduler:quartz)
BuildRequires: mvn(org.testng:testng)
BuildRequires: mvn(rome:rome)
BuildRequires: mvn(toplink.essentials:toplink-essentials)
BuildRequires: mvn(velocity:velocity)
BuildRequires: mvn(velocity-tools:velocity-tools-view)

BuildRequires: mvn(javax.servlet:jstl)
BuildRequires: mvn(taglibs:standard)
%if 0%{?fedora} > 19
BuildRequires: mvn(hsqldb:hsqldb:1)
BuildRequires: mvn(org.jruby:jruby)
%else
BuildRequires: mvn(hsqldb:hsqldb)
BuildRequires: mvn(org.jruby:shared)
%endif
BuildRequires: mvn(xmlunit:xmlunit)

BuildRequires: maven-local
BuildRequires: maven-plugin-bundle
BuildRequires: maven-source-plugin

BuildArch:     noarch


%description
Spring is a layered Java/J2EE application framework, based on code published in
Expert One-on-One J2EE Design and Development by Rod Johnson (Wrox, 2002). 

%package javadoc
Summary:       Javadoc for %{name}

%description javadoc
This package contains javadoc for %{name}.

%package aop
Summary:       Spring Aspect Oriented Framework

%description aop
Spring AOP is an enabling technology that allows the implementation of custom
aspects and provides declarative transaction management without EJB.

%package beans
Summary:       Spring Bean Factory
Requires:      mvn(javax.inject:javax.inject)
Requires:      mvn(org.apache.tomcat:tomcat-el-api)

%description beans
The Spring Bean Factory provides an advanced configuration mechanism capable of
managing beans of any nature, using potentially any kind of storage facility.

%package context
Summary:       Spring Application Context
Requires:      mvn(javax.inject:javax.inject)

%description context
The Spring Application Context is a complete superset of a bean factory, and
adds enhanced capabilities to it, some of them more J2EE and
enterprise-centric.

%package context-support
Summary:       Spring Context Support
Requires:      mvn(net.sf.ehcache:ehcache-core)

%description context-support
This package provide Quartz/CommonJ scheduling,
UI templating, mail and caching.

%package expression
Summary:       Spring Expression Language (SpEL)

%description expression
The Spring Expression Language (SpEL for short) is a powerful expression
language that supports querying and manipulating an object graph at runtime.

%package instrument
Summary:       Spring Instrumentation

%description instrument
The Spring Instrumentation Framework exposes performance and
resource utilization metrics for the Spring container and
gives you runtime control of the container.

%package instrument-tomcat
Summary:       Spring Instrument Tomcat Weaver
Requires:      mvn(org.apache.tomcat:tomcat-catalina)

%description instrument-tomcat
Extension of Tomcat's default class loader which
adds instrumentation to loaded classes without the
need to use a VM-wide agent.

%package jdbc
Summary:       Spring JDBC
%if 0%{?fedora} > 19
Requires:      mvn(hsqldb:hsqldb:1)
%endif

%description jdbc
Spring JDBC takes care of all the low-level details associated to the
development with JDBC.

%package jms
Summary:       Spring jms
Requires:      mvn(org.apache.geronimo.specs:geronimo-jms_1.1_spec)
Requires:      mvn(org.apache.geronimo.specs:geronimo-jta_1.1_spec)

%description jms
This package provide Java Message Service 1.0.2/1.1 support.

%package orm
Summary:       Spring ORM
Requires:      hibernate3 >= 3.6.10-7
Requires:      hibernate3-entitymanager >= 3.6.10-7
Requires:      mvn(org.hibernate.javax.persistence:hibernate-jpa-2.0-api)

%description orm
This package provide JDO support, JPA support, Hibernate
support, TopLink support, iBATIS support.

%package oxm
Summary:       Spring OXM
Requires:      mvn(aopalliance:aopalliance)

%description oxm
This package provide marshaling and unmarshalling
for XML with JAXB context and JiBX binding factories.

%package struts
Summary:       Spring Web Struts
Requires:      mvn(taglibs:standard)
Requires:      mvn(org.apache.tomcat:tomcat-jsp-api)
Requires:      mvn(org.apache.tomcat:tomcat-servlet-api)

%description struts
This package provide integrate a Struts
application with Spring

%package test
Summary:       Spring test context framework

%description test
Spring's test context framework. Also includes common Servlet and
Portlet API mocks.

%package tx
Summary:       Spring Transaction Management

%description tx
Spring provides a consistent abstraction for transaction management that
provides a consistent programming model across different transaction APIs,
supports declarative transaction management, provides a simpler API for
programmatic transaction management and integrates with Spring's various data
access abstractions.

%package web
Summary:       Spring Web
Requires:      mvn(javax.portlet:portlet-api)
Requires:      mvn(org.apache.tomcat:tomcat-jsp-api)

%description web
This package provide web application context, multipart
resolver, HTTP-based remoting support.

%package webmvc
Summary:       Spring Web Servlet
Requires:      mvn(javax.servlet:jstl)
Requires:      mvn(org.apache.geronimo.specs:geronimo-jta_1.1_spec)
Requires:      mvn(org.apache.geronimo.specs:geronimo-validation_1.0_spec)
Requires:      mvn(org.apache.tomcat:tomcat-el-api)
Requires:      mvn(org.apache.tomcat:tomcat-jsp-api)
Requires:      mvn(org.apache.tomcat:tomcat-servlet-api)

%description webmvc
This package provide framework servlets, web MVC framework,
web controllers, web views for JSP, Velocity, Tiles,
iText and POI.

%package webmvc-portlet
Summary:       Spring Web Portlet
Requires:      mvn(javax.portlet:portlet-api)
Requires:      mvn(org.apache.tomcat:tomcat-el-api)
Requires:      mvn(org.apache.tomcat:tomcat-jsp-api)
Requires:      mvn(org.apache.tomcat:tomcat-servlet-api)

%description webmvc-portlet
This package provide support development of Portlet
applications with Spring.

%prep
%setup -q -n spring-framework-%{namedversion}
find -name "*.class" -delete
find -name "*.jar" -print -delete
%patch0 -p1
%patch1 -p1
%patch2 -p0
%patch3 -p0
%patch4 -p0
%patch5 -p0
%patch6 -p0
%patch7 -p0
%patch8 -p0
%patch9 -p1
%patch10 -p1
%patch11 -p1
%patch12 -p1
%patch13 -p1
%patch14 -p1

cp -p %{SOURCE1} pom.xml

# Remove org.springframework.build.aws.maven
%pom_xpath_remove "pom:build/pom:extensions" org.springframework.spring-parent

# ERROR: XThis is not public in Bsh
rm org.springframework.context/src/main/java/org/springframework/scripting/bsh/BshScriptFactory.java
rm org.springframework.context/src/main/java/org/springframework/scripting/bsh/BshScriptUtils.java

# Remove classes which explicitly require Quartz 1.x (others are patched)
rm org.springframework.context.support/src/main/java/org/springframework/scheduling/quartz/JobDetailBean.java
rm org.springframework.context.support/src/main/java/org/springframework/scheduling/quartz/SimpleTriggerBean.java
rm org.springframework.context.support/src/main/java/org/springframework/scheduling/quartz/CronTriggerBean.java

# Remove the dependency on WebSphere UOW as it is not open source and we will
# never be able to build it:
%pom_remove_dep com.ibm.websphere:com.springsource.com.ibm.websphere.uow org.springframework.transaction
rm org.springframework.transaction/src/main/java/org/springframework/transaction/jta/WebSphereUowTransactionManager.java \
 org.springframework.transaction/src/test/java/org/springframework/transaction/jta/WebSphereUowTransactionManagerTests.java

# Don't depend on backport-util-concurrent
%pom_remove_dep :backport-util-concurrent org.springframework.context
sed -i s/edu.emory.mathcs.backport.// `find org.springframework.context -name *.java`

%pom_xpath_set "pom:dependencies/pom:dependency[pom:artifactId = 'jasperreports']/pom:groupId" net.sf.jasperreports org.springframework.web.servlet

%pom_xpath_set "pom:dependencies/pom:dependency[pom:groupId = 'org.codehaus.woodstox']/pom:artifactId" woodstox-core-asl org.springframework.core

%pom_xpath_set "pom:dependencies/pom:dependency[pom:groupId = 'org.codehaus.groovy']/pom:artifactId" groovy org.springframework.context
%pom_xpath_set "pom:dependencies/pom:dependency[pom:groupId = 'org.hibernate']/pom:artifactId" hibernate-validator org.springframework.context

# TODO Fix jruby aId
%if 0%{?fedora} <= 19
%pom_xpath_set "pom:dependencies/pom:dependency[pom:groupId = 'org.jruby']/pom:artifactId" shared org.springframework.context
%else
# Make sure we require version '1' of hsqldb
while read f
do

%pom_xpath_set "pom:dependencies/pom:dependency[pom:groupId = 'hsqldb']/pom:version" 1 ${f}

done << EOF
org.springframework.context.support/pom.xml
org.springframework.integration-tests/pom.xml
org.springframework.jdbc/pom.xml
org.springframework.orm/pom.xml
org.springframework.test/pom.xml
EOF
%endif
%pom_add_dep org.jruby.extras:bytelist:1.0.8:compile org.springframework.context

%pom_xpath_set "pom:dependencyManagement/pom:dependencies/pom:dependency[pom:groupId = 'javax.inject']/pom:artifactId" javax.inject  org.springframework.spring-parent
%pom_xpath_set "pom:dependencies/pom:dependency[pom:artifactId = 'c3p0']/pom:groupId" com.mchange org.springframework.jdbc

%pom_remove_dep org.codehaus.jsr166-mirror:jsr166 org.springframework.context
%pom_remove_dep javax.activation:activation org.springframework.test
%pom_remove_dep org.hibernate:hibernate-cglib-repack org.springframework.test

#%%pom_add_dep junit:junit:4.11:compile org.springframework.test
# require for build test module
%pom_xpath_remove "pom:dependencyManagement/pom:dependencies/pom:dependency[pom:artifactId = 'junit']/pom:scope" org.springframework.spring-parent
# TODO
%pom_remove_dep :jopt-simple org.springframework.core
rm -r org.springframework.core/src/main/java/org/springframework/core/env/JOptCommandLinePropertySource.java

%pom_xpath_set "pom:dependencies/pom:dependency[pom:groupId = 'org.apache.tomcat']/pom:artifactId" tomcat-catalina org.springframework.instrument.tomcat 
%pom_xpath_set "pom:dependencies/pom:dependency[pom:groupId = 'org.apache.tomcat']/pom:version" 7.0.42 org.springframework.instrument.tomcat

# Disable part of Derby support, require derby 10.5
# unavailable method purgeDatabase in org.apache.derby.impl.io.VFMemoryStorageFactory
rm -r org.springframework.jdbc/src/main/java/org/springframework/jdbc/datasource/embedded/DerbyEmbeddedDatabaseConfigurer.java
sed -i "s|case DERBY:||" \
 org.springframework.jdbc/src/main/java/org/springframework/jdbc/datasource/embedded/EmbeddedDatabaseConfigurerFactory.java
sed -i "s|return DerbyEmbeddedDatabaseConfigurer.getInstance();||" \
 org.springframework.jdbc/src/main/java/org/springframework/jdbc/datasource/embedded/EmbeddedDatabaseConfigurerFactory.java

# package com.fasterxml.jackson.databind does not exist
%pom_add_dep com.fasterxml.jackson.core:jackson-databind:2.2.2:compile org.springframework.jms

# Unavailable dep
rm -rf org.springframework.orm/src/main/java/org/springframework/orm/ibatis/*
# Use hibernate3 this release dont provides a real H4 support
rm -rf org.springframework.orm/src/main/java/org/springframework/orm/hibernate4/*

# Make sure we require version '3' of Hibernate
while read f
do

%pom_xpath_remove "pom:dependencies/pom:dependency[pom:groupId = 'org.hibernate']/pom:version" ${f}
%pom_xpath_inject "pom:dependencies/pom:dependency[pom:groupId = 'org.hibernate']" "<version>3</version>" ${f}

done << EOF
org.springframework.test/pom.xml
org.springframework.integration-tests/pom.xml
org.springframework.orm/pom.xml
EOF

# Fix cglib aId
while read p
do

%pom_xpath_set "pom:dependencies/pom:dependency[pom:groupId = 'cglib']/pom:artifactId" cglib ${p}

done << EOF
org.springframework.beans/pom.xml
org.springframework.aop/pom.xml
org.springframework.context/pom.xml
org.springframework.web.servlet/pom.xml
EOF

while read p
do

%pom_remove_dep javax.xml.ws:jaxws-api ${p}

done << EOF
org.springframework.context/pom.xml
org.springframework.spring-parent/pom.xml
org.springframework.web/pom.xml
EOF

cp -p build-spring-framework/resources/* .

%build

%mvn_package ":spring-parent" %{name}
%mvn_package ":spring-core" %{name}
%mvn_package :spring-project __noinstall
# Build without the tests, as they bring a lot of dependecies that are not
# available in the distribution at the moment:
%mvn_build -f -s -- -Dproject.build.sourceEncoding=ISO-8859-1

%install
%mvn_install

%files -f .mfiles-%{name}
%dir %{_javadir}/%{name}
%doc README.md changelog.txt license.txt notice.txt readme.txt

%files javadoc -f .mfiles-javadoc
%doc license.txt notice.txt

%files aop -f .mfiles-spring-aop
%doc license.txt notice.txt

%files beans -f .mfiles-spring-beans
%doc license.txt notice.txt

%files context -f .mfiles-spring-context
%doc license.txt notice.txt

%files context-support -f .mfiles-spring-context-support
%doc license.txt notice.txt

%files expression -f .mfiles-spring-expression
%doc license.txt notice.txt

%files instrument -f .mfiles-spring-instrument
%doc license.txt notice.txt

%files instrument-tomcat -f .mfiles-spring-instrument-tomcat
%doc license.txt notice.txt

%files jdbc -f .mfiles-spring-jdbc
%doc license.txt notice.txt

%files jms -f .mfiles-spring-jms
%doc license.txt notice.txt

%files orm -f .mfiles-spring-orm
%doc license.txt notice.txt

%files oxm -f .mfiles-spring-oxm
%doc license.txt notice.txt

%files struts -f .mfiles-spring-struts
%doc license.txt notice.txt

%files test -f .mfiles-spring-test
%doc license.txt notice.txt

%files tx -f .mfiles-spring-tx
%doc license.txt notice.txt

%files web -f .mfiles-spring-web
%doc license.txt notice.txt

%files webmvc -f .mfiles-spring-webmvc
%doc license.txt notice.txt

%files webmvc-portlet -f .mfiles-spring-webmvc-portlet
%doc license.txt notice.txt

%changelog
* Fri Dec 06 2013 gil cattaneo <puntogil@libero.it> 0:3.1.4-2
- fix for rhbz: 993376, 953977
- switch to XMvn
- disable derby (partial), and jopt-simple support
- enable castor and jruby support

* Thu Dec 5 2013 Orion Poplawski <orion@cora.nwra.com> - 0:3.1.4-1
- Update to 3.1.4
- Add BR xmlunit
- Change wstx-asl to woodstox-core-asl

* Sun Aug 04 2013 Fedora Release Engineering <rel-eng@lists.fedoraproject.org> - 0:3.1.1-15
- Rebuilt for https://fedoraproject.org/wiki/Fedora_20_Mass_Rebuild

* Fri Feb 15 2013 Fedora Release Engineering <rel-eng@lists.fedoraproject.org> - 0:3.1.1-14
- Rebuilt for https://fedoraproject.org/wiki/Fedora_19_Mass_Rebuild

* Wed Feb 06 2013 Java SIG <java-devel@lists.fedoraproject.org> - 0:3.1.1-13
- Update for https://fedoraproject.org/wiki/Fedora_19_Maven_Rebuild
- Replace maven BuildRequires with maven-local

* Tue Jan  8 2013 Mikolaj Izdebski <mizdebsk@redhat.com> - 0:3.1.1-12
- Don't depend on backport-util-concurrent

* Wed Nov 07 2012 Marek Goldmann <mgoldman@redhat.com> - 0:3.1.1-11
- Add support for new Maven compat version resolver (hibernate3)

* Thu Aug  9 2012 Andy Grimm <agrimm@gmail.com> 0:3.1.1-10
- Enable ehcache and quartz in context-support module

* Thu Aug  2 2012 Andy Grimm <agrimm@gmail.com> 0:3.1.1-9
- Fix broken Requires line in struts subpackage

* Tue Jul 31 2012 gil cattaneo <puntogil@libero.it> 0:3.1.1-8
- Enable new modules:  
- spring-context-support, spring-oxm, spring-web,
- spring-jms, spring-orm, spring-webmvc,
- spring-webmvc-portlet, spring-struts

* Sat Jul 21 2012 Fedora Release Engineering <rel-eng@lists.fedoraproject.org> - 0:3.1.1-7
- Rebuilt for https://fedoraproject.org/wiki/Fedora_18_Mass_Rebuild

* Wed May 9 2012 Juan Hernandez <juan.hernandez@redhat.com> 0:3.1.1-6
- Don't own the maven fragments directory (rhbz#819804)
- Add requirement on jpackage-utils

* Tue May 8 2012 Juan Hernandez <juan.hernandez@redhat.com> 0:3.1.1-5
- Move the maven fragments to the subpackages (rhbz#819804)

* Sat Apr 21 2012 Juan Hernandez <juan.hernandez@redhat.com> 0:3.1.1-3
- Own the /usr/share/java/springframework directory (rhbz#814934)
- Remove patch used to deal with missing tomcat POM files

* Thu Mar 15 2012 Juan Hernandez <juan.hernandez@redhat.com> 0:3.1.1-2
- Cleanup of the spec file

* Thu Mar 1 2012 Andy Grimm <agrimm@gmail.com> 0:3.1.1-1
- Initial build

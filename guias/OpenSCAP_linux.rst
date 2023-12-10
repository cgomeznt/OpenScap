
Open-Scap Hardening server
============

https://infosecwriteups.com/server-hardening-with-openscap-be072ba2e415

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/sect-using_oscap

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/security_guide/sect-using_openscap_to_remediate_the_system


dnf insstall openscap-scanner.x86_64 openscap-utils.x86_64 openscap-report.noarch

# oscap xccdf eval --fetch-remote-resources --profile xccdf_org.ssgproject.content_profile_cis --results initial_scan.xml --report initial_scan.html /usr/share/xml/scap/ssg/content/ssg-rhel9-ds.xml

# oscap xccdf eval --remediate --fetch-remote-resources --profile xccdf_org.ssgproject.content_profile_cis --results scan.xml --report scan.html /usr/share/xml/scap/ssg/content/ssg-rl9-ds.xml



Instalar Open-Scap en Windows
==============================

Windows Server 2019
---------------------
Nos apoyamos del siguiente LINK: https://gist.github.com/PSJoshi/4648a4d9ddfae6375213e4e1b2895a81

El siguiente LINK es para la descarga: https://github.com/OpenSCAP/openscap/releases/download/1.3.0/OpenSCAP-1.3.0-win32.msi

Descomprimismos el instalador y procedemos a instalar.

Vamos al siguiente LINK para descargar la plantilla del Sistema Operativo: https://public.cyber.mil/stigs/scap/

Descomprimimos la plantilla y luego ejecutamos el comando info sobre la plantilla para descubrir los Profiles.

Ejecutamos el info para ver los Profiles::

	.\oscap.exe info U_MS_Windows_Server_2019_V2R5_STIG_SCAP_1-2_Benchmark.xml
	
En resultado del comando anterior buscamos los Profiles y utilizamos uno, como por ejemplo::

	https://public.cyber.mil/stigs/scap/

Por ultimo nos vamos a la ruta de instalación y ejecutamos el siguiente comando::

	.\oscap.exe xccdf eval --profile xccdf_mil.disa.stig_profile_MAC-1_Classified --results c:\tmp\initial_scan.xml --report c:\tmp\initial_scan.html U_MS_Windows_Server_2019_V2R5_STIG_SCAP_1-2_Benchmark.xml


Para Windows 11 es
-------------------------

	oscap.exe xccdf eval --profile xccdf_mil.disa.stig_profile_MAC-1_Classified --results c:\tmp\initial_scan.xml --report c:\tmp\initial_scan.html C:\tmp\U_MS_Windows_11_V1R3_STIG_SCAP_1-2_Benchmark.xml
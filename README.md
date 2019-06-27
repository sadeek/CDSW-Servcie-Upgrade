# CDSW-Servcie-Upgrade
"etc/passwd: permission denied"


Error : + echo 'Loading images...'

docker load -i /var/lib/cdsw/opt_cloudera_symlink/parcels/CDSW-1.5.0.p1.849870/images/cdsw_1.5.0.849870_4b1d6ac.tar.gz
ApplyLayer exit status 1 stdout: stderr: open /etc/passwd: permission denied
die_on_error 1 'Unable to load images from [/var/lib/cdsw/opt_cloudera_symlink/parcels/CDSW-1.5.0.p1.849870/images/cdsw_1.5.0.849870_4b1d6ac.tar.gz]. Please make sure that you have sufficient space under '''/var/lib/docker/tmp'''.'
result=1
shift
err_msg='Unable to load images from [/var/lib/cdsw/opt_cloudera_symlink/parcels/CDSW-1.5.0.p1.849870/images/cdsw_1.5.0.849870_4b1d6ac.tar.gz]. Please make sure that you have sufficient space under '''/var/lib/docker/tmp'''.'
'[' 1 -eq 0 ']'
echo -e '\nERROR:: Unable to load images from [/var/lib/cdsw/opt_cloudera_symlink/parcels/CDSW-1.5.0.p1.849870/images/cdsw_1.5.0.849870_4b1d6ac.tar.gz]. Please make sure that you have sufficient space under '''/var/lib/docker/tmp'''.: 1'
exit 1
Note : this error was misleading, this issue was causing by Macfee endpoint

Solution :

We decided to disable these McAfee end point services, it so it doesn't interrupt with our startup next time when the host reboots.

Please stop below macfee endpint service and restart all CDSW service

#systemctl disable isecespd.service
#systemctl disable isectpd.service
#systemctl disable mfefmpd.service


Once you stop these services CDSW service will start operating normally, You can login to CDSW Console and test/try to run some test code.
Run below to verify
#kubectl get pods

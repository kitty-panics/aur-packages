SERVER=223.5.5.5
SMARTDNS_SPEEDTEST_MODE=ping,tcp:80
NEWLINE=UNIX

raw:
	sed -e 's|^server=/\(.*\)/114.114.114.114$$|\1|' accelerated-domains.china.conf | grep -Ev '^#' > accelerated-domains.china.raw.txt

dnscrypt-proxy: raw
	sed -e 's|\(.*\)|\1 $(SERVER)|' accelerated-domains.china.raw.txt > dnscrypt-proxy-forwarding-rules.txt
ifeq ($(NEWLINE),DOS)
	sed -i 's/\r*$$/\r/' dnscrypt-proxy-forwarding-rules.txt
endif

clean:
	rm -f accelerated-domains.china.raw.txt dnscrypt-proxy-forwarding-rules.txt

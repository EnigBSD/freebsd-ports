# Created by: Mario Sergio Fujikawa Ferreira <lioux@FreeBSD.org>

PORTNAME=	dnspython
PORTVERSION=	2.2.1
PORTEPOCH=	1
CATEGORIES=	dns python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	bofh@FreeBSD.org
COMMENT=	DNS toolkit for Python

LICENSE=	ISCL
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}setuptools_scm>=3.4.3:devel/py-setuptools_scm@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}wheel>0:devel/py-wheel@${PY_FLAVOR}

USES=		python:3.6+
USE_PYTHON=	autoplist cython distutils

NO_ARCH=	yes

PORTEXAMPLES=	ddns.py e164.py mx.py name.py reverse.py reverse_name.py xfr.py \
		zonediff.py

OPTIONS_DEFINE=		CURIO DNSSEC DOH EXAMPLES IDNA TRIO
CURIO_DESC=		Coroutine-based library Support
DNSSEC_DESC=		DNSSEC Support
DOH_DESC=		DNS over HTTPS Support
IDNA_DESC=		Internationalizede Domain Names in Application Support
TRIO_DESC=		TRIO Support
CURIO_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}curio>=1.2:devel/py-curio@${PY_FLAVOR} \
			${PYTHON_PKGNAMEPREFIX}sniffio>=1.1:devel/py-sniffio@${PY_FLAVOR}
DNSSEC_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}cryptography>=2.6:security/py-cryptography@${PY_FLAVOR}
DOH_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}h2>0:www/py-h2@${PY_FLAVOR} \
			${PYTHON_PKGNAMEPREFIX}httpx>=0.21.10:www/py-httpx@${PY_FLAVOR} \
			${PYTHON_PKGNAMEPREFIX}requests-toolbelt>0:www/py-requests-toolbelt@${PY_FLAVOR} \
			${PYTHON_PKGNAMEPREFIX}requests>0:www/py-requests@${PY_FLAVOR}
	# Requires h2>=4.1.0
IDNA_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}idna>=2.1:dns/py-idna@${PY_FLAVOR}
TRIO_RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}trio>=0.14.0:net/py-trio@${PY_FLAVOR}

post-install-EXAMPLES-on:
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${PORTEXAMPLES:S,^,${WRKSRC}/examples/,} ${STAGEDIR}${EXAMPLESDIR}

do-test:
	cd ${WRKSRC}/tests && ${SETENV} ${TEST_ENV} ${PYTHON_CMD} utest.py

.include <bsd.port.mk>

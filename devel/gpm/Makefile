# Created by: Luke Jee <lukejee@gmail.com>

PORTNAME=	gpm
PORTVERSION=	1.4.0
DISTVERSIONPREFIX=	v
PORTREVISION=	1
CATEGORIES=	devel

MAINTAINER=	lukejee@gmail.com
COMMENT=	Go Package Manager

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	bash:shells/bash

USES=		go:run

USE_GITHUB=	yes
GH_ACCOUNT=	pote

NO_BUILD=	yes

NO_ARCH=	yes

PLIST_FILES=	bin/gpm

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/bin/gpm ${STAGEDIR}${PREFIX}/bin/

.include <bsd.port.mk>

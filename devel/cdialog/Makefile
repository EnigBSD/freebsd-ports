PORTNAME=	cdialog
DISTVERSION=	1.3-20220117
PORTEPOCH=	2
CATEGORIES=	devel
MASTER_SITES=	ftp://ftp.invisible-island.net/pub/${PORTNAME:S|^c||}/\
		https://invisible-mirror.net/archives/${PORTNAME:S|^c||}/
DISTNAME=	${PORTNAME:S|^c||}-${PORTVERSION:R}-${PORTVERSION:E}

MAINTAINER=	jcpierri@gmail.com
COMMENT=	Enhanced version of 'dialog' to work with ncurses

LICENSE=	LGPL21
LICENSE_FILE=	${WRKSRC}/COPYING

USES=		libtool:build ncurses tar:tgz
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--enable-widec \
		--includedir=${PREFIX}/include/${PORTNAME} \
		--with-libtool \
		--with-${NCURSES_IMPL} \
		--with-package=${PORTNAME}\
		--with-curses-dir=${NCURSESBASE}
MAKEFILE=	makefile
INSTALL_TARGET=	install-strip install-man install-lib
OPTIONS_DEFINE=	EXAMPLES

pre-patch-EXAMPLES-on:
	@${FIND} ${WRKSRC}/samples/ -type f -exec ${REINPLACE_CMD} -i "" "s|dialog|cdialog|g" {} \;

pre-install:
	@${STRIP_CMD} ${WRKSRC}/.libs/libcdialog.so.15.0.0

post-install-EXAMPLES-on:
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	cd ${WRKSRC}/samples && ${COPYTREE_SHARE} . ${STAGEDIR}${EXAMPLESDIR}

.include <bsd.port.mk>

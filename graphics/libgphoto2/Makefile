# Created by: Anders Nordby <anders@fix.no>

PORTNAME=	libgphoto2
PORTVERSION=	2.5.26
PORTREVISION=	2
CATEGORIES=	graphics
MASTER_SITES=	SF/gphoto/libgphoto/${PORTVERSION}

MAINTAINER=	danfe@FreeBSD.org
COMMENT=	Universal digital camera control library

LICENSE=	LGPL21+
LICENSE_FILE=	${WRKSRC}/COPYING

LIB_DEPENDS=	libltdl.so:devel/libltdl

USES=		compiler:c11 gmake gnome iconv libtool localbase pathfix \
		pkgconfig tar:bzip2
USE_CSTD=	gnu99
USE_GNOME=	libxml2

GNU_CONFIGURE=	yes
CONFIGURE_ENV=	LTDLINCL="-I${LOCALBASE}/include" \
		LIBLTDL="-L${LOCALBASE}/lib -lltdl" \
		PATH="${PATH:C,${HOME}/bin,,}" \
		ac_cv_path_DOT=false \
		ac_cv_path_DOXYGEN=false \
		udevscriptdir=${WRKDIR}
INSTALL_TARGET=	install-strip
USE_LDCONFIG=	yes
PATHFIX_MAKEFILEIN=	Makefile.in \
			configure \
			libgphoto2_port/Makefile.in \
			libgphoto2_port/configure

PLIST_SUB=	VERSION="${PORTVERSION}" VERSION_PORT=0.12.0

OPTIONS_DEFINE=	CURL DOCS GD JPEG LIBEXIF NLS
OPTIONS_DEFAULT=	CURL GD JPEG LIBEXIF
OPTIONS_SUB=	yes

CURL_DESC=	Lumix WiFi support via cURL
CURL_LIB_DEPENDS=	libcurl.so:ftp/curl
CURL_CONFIGURE_OFF=	--with-libcurl=no

GD_DESC=	libGD conversion support
GD_LIB_DEPENDS=		libgd.so:graphics/gd
GD_CONFIGURE_OFF=	--with-gdlib=no

JPEG_DESC=	JPEG image mangling support
JPEG_USES=		jpeg
JPEG_CONFIGURE_WITH=	jpeg

LIBEXIF_LIB_DEPENDS=	libexif.so:graphics/libexif
LIBEXIF_CONFIGURE_OFF=	--with-libexif=no

NLS_USES=		gettext
NLS_CONFIGURE_ENABLE=	nls

post-patch:
.for i in configure libgphoto2_port/configure
	@${REINPLACE_CMD} -e \
		'/FLAGS/s|-g|| ; \
		 /grep -i linux/s|; fi ; then|; else false; fi ; then|' \
		${WRKSRC}/${i}
.endfor
	@${REINPLACE_CMD} -e \
		'/^doc_DATA/s|COPYING||' \
		${WRKSRC}/Makefile.in
	@${REINPLACE_CMD} -e \
		'/^SUBDIRS/s|linux-hotplug||' \
		${WRKSRC}/packaging/Makefile.in

.include <bsd.port.mk>

PORTNAME=	kaddressbook
DISTVERSION=	${KDE_APPLICATIONS_VERSION}
PORTREVISION=	1
CATEGORIES=	deskutils kde kde-applications

MAINTAINER=	kde@FreeBSD.org
COMMENT=	KDE contact manager

LIB_DEPENDS=	libassuan.so:security/libassuan \
		libgpg-error.so:security/libgpg-error \
		libgpgme.so:security/gpgme \
		libgpgmepp.so:security/gpgme-cpp \
		libqgpgme.so:security/gpgme-qt5

USES=		cmake compiler:c++11-lib desktop-file-utils gettext grantlee:5 kde:5 \
		qt:5 tar:xz
USE_KDE=	auth codecs completion config configwidgets coreaddons crash \
		i18n iconthemes itemmodels jobwidgets kcmutils kio parts \
		prison service solid sonnet textwidgets widgetsaddons windowsystem xmlgui \
		ecm_build
# pim components
USE_KDE+=	akonadi akonadicontacts akonadisearch contacts grantleetheme \
		imap kontactinterface libkdepim mime pimcommon \
		kdepim-runtime5_run
USE_QT=		concurrent core dbus gui network printsupport widgets xml \
		buildtools_build qmake_build
USE_LDCONFIG=	yes

DESCR=		${.CURDIR:H:H}/deskutils/kdepim/pkg-descr

OPTIONS_DEFINE=	DOCS

.include <bsd.port.mk>

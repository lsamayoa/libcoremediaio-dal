cmake_minimum_required(VERSION 3.17)
project(coremediaio-dal)

include(GNUInstallDirs)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -stdlib=libc++ -std=c++11")

find_library(AVFOUNDATION AVFoundation)
find_library(COCOA Cocoa)
find_library(COREFOUNDATION CoreFoundation)
find_library(COREMEDIA CoreMedia)
find_library(COREVIDEO CoreVideo)
find_library(COCOA Cocoa)
find_library(COREMEDIAIO CoreMediaIO)
find_library(IOSURFACE IOSurface)
find_library(IOKIT IOKit)

include_directories(${AVFOUNDATION}
                    ${COCOA}
                    ${COREFOUNDATION}
                    ${COREMEDIA}
                    ${COREVIDEO}
                    ${COREMEDIAIO}
                    ${COCOA}
                    ${IOSURFACE}
                    include)

set(coremediaio-dal_HEADERS
    include/CAAudioValueRange.h
    include/CAAutoDisposer.h
    include/CACFArray.h
    include/CACFData.h
    include/CACFDictionary.h
    include/CACFDistributedNotification.h
    include/CACFMachPort.h
    include/CACFNumber.h
    include/CACFObject.h
    include/CACFPreferences.h
    include/CACFString.h
    include/CADebugMacros.h
    include/CADebugPrintf.h
    include/CAException.h
    include/CAGuard.h
    include/CAHostTimeBase.h
    include/CALogMacros.h
    include/CAMutex.h
    include/CAPThread.h
    include/CAProcess.h
    include/CATokenMap.h
    include/CAVolumeCurve.h
    include/CMIODebugMacros.h
    include/CMIODebugPrintf.h
    include/CMIO_Buffer.h
    include/CMIO_CMA_BlockBuffer.h
    include/CMIO_CMA_FormatDescription.h
    include/CMIO_CMA_SampleBuffer.h
    include/CMIO_CMA_SimpleQueue.h
    include/CMIO_CMA_Time.h
    include/CMIO_CVA_Buffer.h
    include/CMIO_CVA_Image_Buffer.h
    include/CMIO_CVA_Pixel_Buffer.h
    include/CMIO_DALA_System.h
    include/CMIO_DP_Command.h
    include/CMIO_DP_Control.h
    include/CMIO_DP_ControlDictionary.h
    include/CMIO_DP_Device.h
    include/CMIO_DP_DeviceCommands.h
    include/CMIO_DP_DeviceSettings.h
    include/CMIO_DP_IOV_Control.h
    include/CMIO_DP_IOV_ControlDictionary.h
    include/CMIO_DP_Object.h
    include/CMIO_DP_PlugIn.h
    include/CMIO_DP_Property_Base.h
    include/CMIO_DP_Property_ClientSyncDiscontinuity.h
    include/CMIO_DP_Property_Clock.h
    include/CMIO_DP_Property_Deck.h
    include/CMIO_DP_Property_DeviceMaster.h
    include/CMIO_DP_Property_EndOfData.h
    include/CMIO_DP_Property_FirstOutputPresentationTimeStamp.h
    include/CMIO_DP_Property_FormatList.h
    include/CMIO_DP_Property_HogMode.h
    include/CMIO_DP_Property_NoData.h
    include/CMIO_DP_Property_OutputBuffers.h
    include/CMIO_DP_Property_SMPTETimeCallback.h
    include/CMIO_DP_Property_ScheduledOutputNotificationProc.h
    include/CMIO_DP_Property_SuspendedByUser.h
    include/CMIO_DP_Stream.h
    include/CMIO_DP_UserInfo.h
    include/CMIO_IOKA_NotificationPort.h
    include/CMIO_IOKA_Object.h
    include/CMIO_IOSA_Assistance.h
    include/CMIO_IOVA_Assistance.h
    include/CMIO_PTA_Assistance.h
    include/CMIO_PTA_CFMachPortThread.h
    include/CMIO_PTA_NotificationPortThread.h
    include/CMIO_PropertyAddress.h
    include/CMIO_SA_Assistance.h
    include/CMIO_SMPTETimeBase.h)

set(coremediaio-dal_SOURCES
    src/CACFArray.cpp
    src/CACFDictionary.cpp
    src/CACFDistributedNotification.cpp
    src/CACFMachPort.cpp
    src/CACFNumber.cpp
    src/CACFPreferences.cpp
    src/CACFString.cpp
    src/CAGuard.cpp
    src/CAHostTimeBase.cpp
    src/CAMutex.cpp
    src/CAPThread.cpp
    src/CAProcess.cpp
    src/CAVolumeCurve.cpp
    src/CMIO_DP_Command.cpp
    src/CMIO_DP_Control.cpp
    src/CMIO_DP_ControlDictionary.cpp
    src/CMIO_DP_Device.cpp
    src/CMIO_DP_DeviceCommands.cpp
    src/CMIO_DP_DeviceSettings.cpp
    src/CMIO_DP_HardwarePlugInInterface.cpp
    src/CMIO_DP_Object.cpp
    src/CMIO_DP_PlugIn.cpp
    src/CMIO_DP_Stream.cpp
    src/CMIO_DP_UserInfo.cpp
    src/CMIO_DP_Property_Base.cpp
    src/CMIO_DP_Property_ClientSyncDiscontinuity.cpp
    src/CMIO_DP_Property_Clock.cpp
    src/CMIO_DP_Property_Deck.cpp
    src/CMIO_DP_Property_DeviceMaster.cpp
    src/CMIO_DP_Property_EndOfData.cpp
    src/CMIO_DP_Property_FirstOutputPresentationTimeStamp.cpp
    src/CMIO_DP_Property_FormatList.cpp
    src/CMIO_DP_Property_HogMode.cpp
    src/CMIO_DP_Property_NoData.cpp
    src/CMIO_DP_Property_OutputBuffers.cpp
    src/CMIO_DP_Property_SMPTETimeCallback.cpp
    src/CMIO_DP_Property_ScheduledOutputNotificationProc.cpp
    src/CMIO_DP_Property_SuspendedByUser.cpp
    src/CMIO_DP_IOV_Control.cpp
    src/CMIO_DP_IOV_ControlDictionary.cpp
    src/CMIODebugMacros.cpp
    src/CMIODebugPrintf.cpp
    src/CMIO_SMPTETimeBase.cpp
    src/CMIO_DALA_System.cpp
    src/CMIO_IOKA_NotificationPort.cpp
    src/CMIO_IOSA_Assistance.cpp
    src/CMIO_SA_Assistance.cpp
    src/CMIO_IOVA_Assistance.cpp
    src/CMIO_PTA_CFMachPortThread.cpp
    src/CMIO_PTA_NotificationPortThread.cpp)

add_library(coremediaio-dal SHARED
    ${coremediaio-dal_SOURCES}
    ${coremediaio-dal_HEADERS})

target_link_libraries(coremediaio-dal
    ${AVFOUNDATION}
    ${COCOA}
    ${COREFOUNDATION}
    ${COREMEDIA}
    ${COREVIDEO}
    ${COREMEDIAIO}
    ${IOSURFACE}
    ${IOKIT})

configure_file(coremediaio-dal.pc.in coremediaio-dal.pc @ONLY)

install(TARGETS coremediaio-dal
    EXPORT        coremediaio-dal
    LIBRARY       DESTINATION "${CMAKE_INSTALL_LIBDIR}"                            COMPONENT shlib
    ARCHIVE       DESTINATION "${CMAKE_INSTALL_LIBDIR}"                            COMPONENT lib
    RUNTIME       DESTINATION "${CMAKE_INSTALL_BINDIR}"                            COMPONENT bin)
install(FILES ${coremediaio-dal_HEADERS}             DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/coremediaio-dal COMPONENT devel)
install(FILES ${CMAKE_BINARY_DIR}/coremediaio-dal.pc DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
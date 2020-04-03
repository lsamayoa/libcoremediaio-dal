cmake_minimum_required(VERSION 3.17)
project(coremediaio-dal)

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
                    include
                    )

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
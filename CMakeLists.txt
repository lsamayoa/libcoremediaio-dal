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
                    CoreAudio/PublicUtility
                    CoreMediaIO/PublicUtility
                    CoreMediaIO/PublicUtility/CoreMediaAssistant
                    CoreMediaIO/PublicUtility/CoreVideoAssistant
                    CoreMediaIO/PublicUtility/DALAssistant
                    CoreMediaIO/PublicUtility/IOKitAssistant
                    CoreMediaIO/PublicUtility/IOSurfaceAssistant
                    CoreMediaIO/PublicUtility/IOVideoAssistant
                    CoreMediaIO/PublicUtility/IOStreamAssistant
                    CoreMediaIO/PublicUtility/POSIXThreadAssistant
                    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base
                    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties
                    CoreMediaIO/DeviceAbstractionLayer/Devices/IOV/PlugIn
                    CoreMediaIO/DeviceAbstractionLayer/Devices/IOV/PlugIn
                    )

set(coremediaio-dal_SOURCES
    CoreAudio/PublicUtility/CACFArray.cpp
    CoreAudio/PublicUtility/CACFDictionary.cpp
    CoreAudio/PublicUtility/CACFDistributedNotification.cpp
    CoreAudio/PublicUtility/CACFMachPort.cpp
    CoreAudio/PublicUtility/CACFNumber.cpp
    CoreAudio/PublicUtility/CACFPreferences.cpp
    CoreAudio/PublicUtility/CACFString.cpp
    CoreAudio/PublicUtility/CAGuard.cpp
    CoreAudio/PublicUtility/CAHostTimeBase.cpp
    CoreAudio/PublicUtility/CAMutex.cpp
    CoreAudio/PublicUtility/CAPThread.cpp
    CoreAudio/PublicUtility/CAProcess.cpp
    CoreAudio/PublicUtility/CAVolumeCurve.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_Command.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_Control.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_ControlDictionary.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_Device.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_DeviceCommands.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_DeviceSettings.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_HardwarePlugInInterface.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_Object.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_PlugIn.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_Stream.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Base/CMIO_DP_UserInfo.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_Base.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_ClientSyncDiscontinuity.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_Clock.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_Deck.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_DeviceMaster.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_EndOfData.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_FirstOutputPresentationTimeStamp.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_FormatList.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_HogMode.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_NoData.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_OutputBuffers.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_SMPTETimeCallback.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_ScheduledOutputNotificationProc.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/DP/Properties/CMIO_DP_Property_SuspendedByUser.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/IOV/PlugIn/CMIO_DP_IOV_Control.cpp
    CoreMediaIO/DeviceAbstractionLayer/Devices/IOV/PlugIn/CMIO_DP_IOV_ControlDictionary.cpp
    CoreMediaIO/PublicUtility/CMIODebugMacros.cpp
    CoreMediaIO/PublicUtility/CMIODebugPrintf.cpp
    CoreMediaIO/PublicUtility/CMIO_SMPTETimeBase.cpp
    CoreMediaIO/PublicUtility/DALAssistant/CMIO_DALA_System.cpp
    CoreMediaIO/PublicUtility/IOKitAssistant/CMIO_IOKA_NotificationPort.cpp
    CoreMediaIO/PublicUtility/IOStreamAssistant/CMIO_IOSA_Assistance.cpp
    CoreMediaIO/PublicUtility/IOSurfaceAssistant/CMIO_SA_Assistance.cpp
    CoreMediaIO/PublicUtility/IOVideoAssistant/CMIO_IOVA_Assistance.cpp
    CoreMediaIO/PublicUtility/POSIXThreadAssistant/CMIO_PTA_CFMachPortThread.cpp
    CoreMediaIO/PublicUtility/POSIXThreadAssistant/CMIO_PTA_NotificationPortThread.cpp)

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
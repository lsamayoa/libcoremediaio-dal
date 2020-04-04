cmake_minimum_required(VERSION 3.16)
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
                    src/CoreAudio
                    src/CoreMediaIO
                    src/CoreMediaIO/DeviceAbstractionLayer/CoreMediaAssistant
                    src/CoreMediaIO/DeviceAbstractionLayer/CoreVideoAssistant
                    src/CoreMediaIO/DeviceAbstractionLayer/DalAssistant
                    src/CoreMediaIO/DeviceAbstractionLayer/Device
                    src/CoreMediaIO/DeviceAbstractionLayer/Device/IOVideo
                    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property
                    src/CoreMediaIO/DeviceAbstractionLayer/IOKitAssistant
                    src/CoreMediaIO/DeviceAbstractionLayer/IOStreamAssistant
                    src/CoreMediaIO/DeviceAbstractionLayer/IOVideoAssistant
                    src/CoreMediaIO/DeviceAbstractionLayer/POSIXThreadAssistant)

set(coremediaio-dal_HEADERS
    src/CoreAudio/CAAudioValueRange.h
    src/CoreAudio/CAAutoDisposer.h
    src/CoreAudio/CACFArray.h
    src/CoreAudio/CACFData.h
    src/CoreAudio/CACFDictionary.h
    src/CoreAudio/CACFDistributedNotification.h
    src/CoreAudio/CACFMachPort.h
    src/CoreAudio/CACFNumber.h
    src/CoreAudio/CACFObject.h
    src/CoreAudio/CACFPreferences.h
    src/CoreAudio/CACFString.h
    src/CoreAudio/CADebugMacros.h
    src/CoreAudio/CADebugPrintf.h
    src/CoreAudio/CAException.h
    src/CoreAudio/CAGuard.h
    src/CoreAudio/CAHostTimeBase.h
    src/CoreAudio/CALogMacros.h
    src/CoreAudio/CAMutex.h
    src/CoreAudio/CAPThread.h
    src/CoreAudio/CAProcess.h
    src/CoreAudio/CATokenMap.h
    src/CoreAudio/CAVolumeCurve.h

    src/CoreMediaIO/DeviceAbstractionLayer/CoreMediaAssistant/CMIO_CMA_BlockBuffer.h
    src/CoreMediaIO/DeviceAbstractionLayer/CoreMediaAssistant/CMIO_CMA_FormatDescription.h
    src/CoreMediaIO/DeviceAbstractionLayer/CoreMediaAssistant/CMIO_CMA_SampleBuffer.h
    src/CoreMediaIO/DeviceAbstractionLayer/CoreMediaAssistant/CMIO_CMA_SimpleQueue.h
    src/CoreMediaIO/DeviceAbstractionLayer/CoreMediaAssistant/CMIO_CMA_Time.h

    src/CoreMediaIO/DeviceAbstractionLayer/CoreVideoAssistant/CMIO_CVA_Buffer.h
    src/CoreMediaIO/DeviceAbstractionLayer/CoreVideoAssistant/CMIO_CVA_Image_Buffer.h
    src/CoreMediaIO/DeviceAbstractionLayer/CoreVideoAssistant/CMIO_CVA_Pixel_Buffer.h

    src/CoreMediaIO/DeviceAbstractionLayer/DalAssistant/CMIO_DALA_System.h

    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Command.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Control.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_ControlDictionary.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Device.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_DeviceCommands.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_DeviceSettings.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Object.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_PlugIn.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Stream.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_UserInfo.h

    src/CoreMediaIO/DeviceAbstractionLayer/Device/IOVideo/CMIO_DP_IOV_Control.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/IOVideo/CMIO_DP_IOV_ControlDictionary.h

    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_Base.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_ClientSyncDiscontinuity.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_Clock.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_Deck.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_DeviceMaster.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_EndOfData.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_FirstOutputPresentationTimeStamp.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_FormatList.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_HogMode.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_NoData.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_OutputBuffers.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_SMPTETimeCallback.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_ScheduledOutputNotificationProc.h
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_SuspendedByUser.h

    src/CoreMediaIO/DeviceAbstractionLayer/IOKitAssistant/CMIO_IOKA_NotificationPort.h
    src/CoreMediaIO/DeviceAbstractionLayer/IOKitAssistant/CMIO_IOKA_Object.h

    src/CoreMediaIO/DeviceAbstractionLayer/IOStreamAssistant/CMIO_IOSA_Assistance.h
   
    src/CoreMediaIO/DeviceAbstractionLayer/IOVideoAssistant/CMIO_IOVA_Assistance.h

    src/CoreMediaIO/DeviceAbstractionLayer/POSIXThreadAssistant/CMIO_PTA_Assistance.h
    src/CoreMediaIO/DeviceAbstractionLayer/POSIXThreadAssistant/CMIO_PTA_CFMachPortThread.h
    src/CoreMediaIO/DeviceAbstractionLayer/POSIXThreadAssistant/CMIO_PTA_NotificationPortThread.h

    src/CoreMediaIO/CMIODebugMacros.h
    src/CoreMediaIO/CMIODebugPrintf.h
    src/CoreMediaIO/CMIO_Buffer.h
    src/CoreMediaIO/CMIO_PropertyAddress.h
    src/CoreMediaIO/CMIO_SMPTETimeBase.h

    src/CoreMediaIO/DeviceAbstractionLayer/IOSurfaceAssistant/CMIO_SA_Assistance.h)

set(coremediaio-dal_SOURCES
    src/CoreAudio/CACFArray.cpp
    src/CoreAudio/CACFDictionary.cpp
    src/CoreAudio/CACFDistributedNotification.cpp
    src/CoreAudio/CACFMachPort.cpp
    src/CoreAudio/CACFNumber.cpp
    src/CoreAudio/CACFPreferences.cpp
    src/CoreAudio/CACFString.cpp
    src/CoreAudio/CAGuard.cpp
    src/CoreAudio/CAHostTimeBase.cpp
    src/CoreAudio/CAMutex.cpp
    src/CoreAudio/CAPThread.cpp
    src/CoreAudio/CAProcess.cpp
    src/CoreAudio/CAVolumeCurve.cpp

    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Command.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Control.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_ControlDictionary.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Device.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_DeviceCommands.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_DeviceSettings.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_HardwarePlugInInterface.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Object.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_PlugIn.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_Stream.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/CMIO_DP_UserInfo.cpp

    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_Base.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_ClientSyncDiscontinuity.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_Clock.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_Deck.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_DeviceMaster.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_EndOfData.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_FirstOutputPresentationTimeStamp.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_FormatList.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_HogMode.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_NoData.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_OutputBuffers.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_SMPTETimeCallback.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_ScheduledOutputNotificationProc.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/Property/CMIO_DP_Property_SuspendedByUser.cpp

    src/CoreMediaIO/DeviceAbstractionLayer/Device/IOVideo/CMIO_DP_IOV_Control.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/Device/IOVideo/CMIO_DP_IOV_ControlDictionary.cpp

    src/CoremediaIO/CMIODebugMacros.cpp
    src/CoremediaIO/CMIODebugPrintf.cpp
    src/CoremediaIO/CMIO_SMPTETimeBase.cpp

    src/CoremediaIO/DeviceAbstractionLayer/DALAssistant/CMIO_DALA_System.cpp

    src/CoreMediaIO/DeviceAbstractionLayer/IOKitAssistant/CMIO_IOKA_NotificationPort.cpp

    src/CoreMediaIO/DeviceAbstractionLayer/IOStreamAssistant/CMIO_IOSA_Assistance.cpp

    src/CoreMediaIO/DeviceAbstractionLayer/IOSurfaceAssistant/CMIO_SA_Assistance.cpp

    src/CoreMediaIO/DeviceAbstractionLayer/IOVideoAssistant/CMIO_IOVA_Assistance.cpp

    src/CoreMediaIO/DeviceAbstractionLayer/POSIXThreadAssistant/CMIO_PTA_CFMachPortThread.cpp
    src/CoreMediaIO/DeviceAbstractionLayer/POSIXThreadAssistant/CMIO_PTA_NotificationPortThread.cpp)

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
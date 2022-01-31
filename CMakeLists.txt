cmake_minimum_required(VERSION 3.0)
project(OpenAL)

set(CSHARP
    Alc/backends/wasapi_winrt_wp8.cpp
)

add_library(OpenAL STATIC
    ${CSHARP}

    OpenAL32/alAuxEffectSlot.c
    OpenAL32/alBuffer.c
    OpenAL32/alEffect.c
    OpenAL32/alError.c
    OpenAL32/alExtension.c
    OpenAL32/alFilter.c
    OpenAL32/alListener.c
    OpenAL32/alSource.c
    OpenAL32/alState.c
    OpenAL32/alThunk.c

    Alc/backends/loopback.c
    Alc/backends/null.c
    Alc/backends/thread_msg_queue_cpp11.cpp
    Alc/backends/xaudio2.cpp

    Alc/ALc.c
    Alc/ALc_cpp11.cpp
    Alc/alcConfig.c
    Alc/alcDedicated.c
    Alc/alcEcho.c
    Alc/alcModulator.c
    Alc/alcReverb.c
    Alc/alcRing.c
    Alc/alcThreadCpp11.cpp
    Alc/ALu.c
    ALc/bs2b.c
    ALc/helpers.c
    ALc/hrtf.c
    ALc/mixer.c
    ALc/panning.c
)

set_source_files_properties(${CSHARP} PROPERTIES COMPILE_FLAGS /ZW)

target_include_directories(OpenAL PRIVATE
    OpenAL32/include
    winrt.vs2015
)

target_compile_definitions(OpenAL PRIVATE
    _CRT_SECURE_NO_WARNINGS
    AL_ALEXT_PROTOTYPES
    strcasecmp=_stricmp
    strncasecmp=_strnicmp
)

target_include_directories(OpenAL PUBLIC include)
target_compile_definitions(OpenAL PUBLIC AL_LIBTYPE_STATIC _WIN_RT)

# ImageMagick | Image Formats

v7.1.2-34 Latest Stable Release

# Image Formats

Explore all supported image formats, pseudo formats, built-in images, patterns, and embedded profiles in ImageMagick.

   Get ImageMagick    Documentation

 quickstart.sh

# Install via your favorite Package Manager

$ brew install imagemagick

# Convert PNG to WebP with compression

$ magick input.png -quality 85 output.webp

# Resize image maintaining aspect ratio

$ magick input.jpg -resize 800x600^ output.jpg

 Colorspaces Supported Formats Pseudo Formats Built-in Images Built-in Patterns Embedded Profiles

 ImageMagick uses an ASCII string known as magick (e.g., GIF) to identify file formats, algorithms, built-in patterns, and embedded profiles.

 To get a complete listing of which image formats are supported on your system, run:

 $ magick identify -list format

 On compatible platforms, extensions like .gz, .Z, .bz2, and .pgp are uncompressed or decrypted automagically.

## A Word about Colorspaces

 Most image formats assume an sRGB colorspace, while others support linear RGB, linear GRAY, CMYK, or LAB. To determine your image colorspace, use:

 $ magick identify -verbose image.jpg
...
Colorspace: sRGB

 $ magick image.jpg -print "%[colorspace]\n" null:
sRGB

## Supported Image Formats

Complete directory of all major file formats supported by ImageMagick.

 Tag Mode Description Notes

AAIRWAAI Dune image

AIRWAdobe Illustrator CS2

APNGRWAnimated Portable Network GraphicsRequires explicit specifier (apng:myImage.apng) and ffmpeg.

ARTRWPFS: 1st PublisherOriginally used on Macintosh/PFS: 1st Publisher clip art.

ARWRSony Digital Camera Alpha Raw Image FormatSet -define dng:use-camera-wb=true to use embedded profile.

AVIRMicrosoft Audio/Visual Interleaved

AVIFRWFormat derived from keyframes of AV1 video

AVSRWAVS X image

BAYERRWRaw mosaiced samplesUse size and depth parameters; support for floats via quantum:format.

BPGRWBetter Portable GraphicsUse quality option.

BMP, BMP2, BMP3RWMicrosoft Windows bitmapDefault version 4. Use BMP3/BMP2 for versions 3 and 2.

BRFWBraille Ready Format6-dot braille matrix encoding.

CALSRContinuous Acquisition and Life-cycle Support Type 1US military blueprint archive format.

CINRWKodak Cineon Image FormatUse -set for gamma, black/white points, and cineon properties.

CIPWCisco IP phone image format

CMYKRWRaw cyan, magenta, yellow, and black samplesUse size/depth; supports float formats.

CMYKARWRaw cyan, magenta, yellow, black, and alpha samplesSupports float formats via quantum:format.

CR2RCanon Digital Camera Raw Image FormatRequires explicit specifier (cr2:image.cr2).

CRWRCanon Digital Camera Raw Image Format

CUBERColor grading preset lookup tablePixel-by-pixel replacement mapping.

CURRMicrosoft Cursor Icon

CUTRDR Halo

C2PARC2PA Provenance Metadata

DCMRDigital Imaging and Communications in Medicine (DICOM)Medical X-ray support; handles window center/width tags.

DCRRDigital Camera Raw Image FileUse DCRAW delegate program.

DCXRWZSoft IBM PC multi-page Paintbrush image

DDSRWMicrosoft Direct Draw SurfaceCompression defines like dxt1, dxt5, and mipmaps.

DEBUGWRaw pixel debug fileFor developers.

DIBRWMicrosoft Windows Device Independent BitmapBMP file without BMP header.

DJVURDjVu Document Format

DMRRWDigital media repositoryRequires MagickCache delegate library.

DNGRDigital NegativeRequires explicit specifier (dng:image.dng).

DOTRGraph VisualizationLayout engine options via defines.

DPXRWSMPTE Digital Moving Picture Exchange 2.0Gamma and black/white point controls.

EMFRMicrosoft Enhanced Metafile (32-bit)Windows only; size option supported.

EPDFRWEncapsulated Portable Document Format

EPIRWAdobe Encapsulated PostScript InterchangeRequires Ghostscript.

EPSRWAdobe Encapsulated PostScriptRequires Ghostscript.

EPS2WAdobe Level II Encapsulated PostScriptRequires Ghostscript.

EPS3WAdobe Level III Encapsulated PostScriptRequires Ghostscript.

EPSFRWAdobe Encapsulated PostScriptRequires Ghostscript.

EPSIRWAdobe Encapsulated PostScript Interchange formatRequires Ghostscript.

EPTRWEncapsulated PostScript with TIFF previewRequires Ghostscript.

EXRRWIndustrial Light & Magic High Dynamic-RangeRequires OpenEXR library.

FARBFELDRWFarbfeld lossless image formatsRGB 16-bit RGBA lossless format.

FAXRWGroup 3 TIFFFixed width 1728; non-square pixels.

FITSRWFlexible Image Transport SystemSupports single and double-precision floats.

FL32RWFilmLight floating point image format

FLIFRWFree Lossless Image Format

FPXRWFlashPix FormatMulti-resolution pyramid storage; requires FlashPix SDK.

FTXTRWMultispectral channels as formatted text

GIFRWCompuServe Graphics Interchange Format8-bit RGB PseudoColor up to 256 palette entries.

GPLTRGnuplot plot filesRequires gnuplot.

GRAYRWRaw gray samplesSupports scanline padding and float/signed options.

GRAYARWRaw gray and alpha samplesSupports float configurations.

GROUP4RWRaw CCITT Group 4 samplesUse size option.

HDRRWRadiance RGBE image formatHigh dynamic range support.

HEICRWApple High Efficiency Image FormatRequires libheif delegate library.

HPGLRHP-GL plotter languageRequires hp2xx.

HRZRWSlow Scan TeleVision

HTMLRWHTML with client-side image mapRequires html2ps to read.

ICORMicrosoft icon (ICON)

INFOWFormat and characteristics of the image

ISOBRLWISO/TR 11548-1 Braille (8-dot)

ISOBRL6WISO/TR 11548-1 Braille (6-dot)

JBIGRWJoint Bi-level Image experts Group (BIE, JBG)Requires jbigkit.

JNGRWMultiple-image Network GraphicsJPEG in PNG-style wrapper with transparency.

JP2RWJPEG-2000 JP2 File Format SyntaxEncoding options via defines.

JPTRWJPEG-2000 Code Stream SyntaxEncoding options via defines.

J2CRWJPEG-2000 Code Stream SyntaxEncoding options via defines.

J2KRWJPEG-2000 Code Stream SyntaxEncoding options via defines.

JPEGRWJoint Photographic Experts Group JFIF formatLossy compression; quality scaling, Huffman, and DCT options.

JSONWJavaScript Object Notation data-interchangeSupports attributes, moments, and features defines.

JXLRWJPEG XL image coding systemRequires JPEG XL delegate library.

JXRRWJPEG extended rangeRequires jxrlib.

KERNELWMorphology kernel format

MANRLinux reference manual pagesRequires groff and Ghostscript.

MATRMATLAB image format

MIFFRWMagick multispectral image file formatPersists all image attributes and channel data.

MONORWBi-level bitmap (LSB order)

MNGRWMultiple-image Network GraphicsPNG-like multi-image animation container.

M2VRWMPEG-2 video formatRequires ffmpeg.

MPEGRWMPEG-1 video formatRequires ffmpeg.

MPCRWMagick Pixel Cache image file formatNative in-memory uncompressed cache format.

MPORMulti-picture Object

MPRRWMagick Persistent RegistryRead/write images directly in memory via registry keys.

MRWRSony (Minolta) Raw Image FileEmbedded profile options via defines.

MSLRWMagick Scripting LanguageXML scripting for conjure utility; requires libxml2.

MTVRWMTV Raytracing image format

MVGRWMagick Vector GraphicsNative vector drawing metafile format.

NEFRNikon Digital SLR Camera Raw Image File

ORFROlympus Digital Camera Raw Image File

ORAROpenRaster layered graphics exchange format

OTBRWOn-the-air Bitmap

P7RWXv's Visual Schnauzer thumbnail format

PALMRWPalm pixmap

PAMWCommon 2-dimensional bitmap format

CLIPBOARDRWWindows ClipboardWindows only.

PBMRWPortable bitmap format (black and white)Netpbm family.

PCDRWPhoto CDMax resolution written 768x512.

PCDSRWPhoto CDDecoded with sRGB color tables.

PCLWHP Page Control LanguageFit-to-page option via defines.

PCXRWZSoft IBM PC Paintbrush file

PDBRWPalm Database ImageViewer Format

PDFRWPortable Document FormatRequires Ghostscript; cropbox, trimbox, and density options.

PEFRPentax Electronic FileRequires explicit specifier (pef:image.pef).

PESREmbrid Embroidery Format

PFARPostscript Type 1 font (ASCII)Returns preview image.

PFBRPostscript Type 1 font (binary)Returns preview image.

PFMRWPortable float map format

PGMRWPortable graymap format (gray scale)Netpbm family.

PHMRWPortable float map format 16-bit half

PICONRWPersonal Icon

PICTRWApple Macintosh QuickDraw/PICT file

PIXRAlias/Wavefront RLE image format

PNG, PNG8, PNG24, PNG32, PNG48, PNG64, PNG00RWPortable Network Graphics variantsRequires libpng; supports indexed, RGB, and RGBA bit depths.

PNMRWPortable anymap familyAutomagically selects PBM, PGM, or PPM representation.

POCKETMODRWPocketmod personal organizer format

PPMRWPortable pixmap format (color)Netpbm family.

PS, PS2, PS3RWAdobe PostScript (Levels I, II, III)Requires Ghostscript.

PSBRWAdobe Large Document Format

PSDRWAdobe Photoshop multispectral bitmap fileSupports alpha blending, adjustment layers, and opacity masks.

PTIFRWPyramid encoded TIFFMulti-resolution pyramid structure.

PWPRSeattle File Works multi-image file

QOIRWQuite OK Image FormatFast, lossless compression.

RADRRadiance image fileRequires ra_ppm.

RAFRFuji CCD-RAW Graphic File

RAWRRaw samples

RGB, RGBARWRaw RGB and RGBA sample streamsSize and depth parameters required.

RGB565RRaw red, green, blue pixels in 5-6-5 format

RGFRWLEGO Mindstorms EV3 Robot Graphics File

RLARAlias/Wavefront image file

RLERUtah Run length encoded image file

SCTRScitex Continuous Tone Picture

SFWRSeattle File Works image

SF3RSimple File Format FamilyLightweight text-based structure.

SGIRWIrix RGB image

SHTMLWHTML client-side image mapBased on montage or tiled output.

SID, MrSIDRMultiresolution seamless imageDecoding delegated to mrsidgeodecode or gdal_translate.

SPARSE-COLORWRaw text file for sparse color options

STRIMGRWString to images and back

SUNRWSUN Rasterfile

SVGRWScalable Vector GraphicsRenders via Inkscape, RSVG, or internal MSVG renderer.

TEXTRText fileRequires explicit specifier (text:README.txt).

TGARWTruevision Targa image (ICB, VDA, VST)

TIFFRWTagged image file multispectral format (TIF)Extensive strip, tile, endian, and compression tag controls.

TIMRPSX TIM file

TTFRTrueType font fileRequires Freetype 2; returns preview image.

TXTRWMultispectral raw text file

UBRL, UBRL6WUnicode Braille (8-dot and 6-dot)

UHDRRWUltra HDRRequires libultrahdr delegate library.

UILWX-Motif UIL table

UYVYRWInterleaved YUV raw image

VICARRWVICAR rasterfile format

VIDEORWVarious video formats (APNG, AVI, MP4, WEBM)Refer to video defines.

VIFFRWKhoros Visualization Image File Format

WBMPRWWireless bitmapUncompressed monochrome only.

WDPRWJPEG extended rangeRequires jxrlib.

WEBPRWWebP image formatRequires WEBP delegate library.

WMFRWindows MetafileRequires libwmf.

WPGRWord Perfect Graphics File

XRWDisplay or import from X11 server

XBMRWX Windows system bitmapBlack and white only.

XCFRGIMP image

XPMRWX Windows system pixmap (PM)Color icons.

XWDRWX Windows system window dumpScreen dumps.

X3FRSigma Camera RAW Picture File

YAMLWHuman-readable data-serialization languageSupports locate, limit, and moment defines.

YCbCr, YCbCrARWRaw Y, Cb, Cr, and alpha samplesSize and depth parameters required.

YUVRWCCIR 601 4:1:1Sampling-factor option supported.

## Pseudo-image Formats

Algorithmic image formats and specialized target pipelines.

 Tag Mode Description Notes

ASHLARWImage sequence laid out in continuous irregular coursesCustom canvas sizing and tile alignment.

CANVASRCanvas image of specified colorSolid color generation via size and color parameters.

CAPTIONRImage captionSupports text splitting via caption:split.

CLIPRWClip path of image

CLIPBOARDRWClipboard

FRACTALRPlasma fractal image

GRADIENTRLinear or radial gradient imageGradual shade transitions.

HALDRIdentity Hald CLUT ImageColor grading lookup tables.

HISTOGRAMWHistogram of the imageOutputs unique colors as comments.

INLINERWBase64-encoded inline imageData URI strings for web integration.

LABELRText image formatText specified directly as filename.

MAPRWColormap intensities and indices

MASKRWGrayscale image mask sequence

MATTEWMATTE formatWrite-only.

NULLRWNULL imageBlank montage tiles and performance evaluation.

OPENWDisplay image to computer screenMacOS X only.

PANGORAdvanced text caption layoutMarkup, justification, and hinting options via defines.

PLASMARPlasma fractal image

PREVIEWWPreview image enhancement or effect rangeParameter selection assistant.

PRINTWSend image to computer printerUses PRINTER or LPDEST variables.

SCANRImport image from scanner deviceRequires SANE.

RADIAL_GRADIENTRGradual radial color passing

SCANXRImport image from default scanner

SCREENSHOTRComputer display content captureMulti-monitor support under Windows.

STEGANORSteganographic imageWidth, height, and offset controls.

TILERTiled image patternResponsive to compose options.

UNIQUEWWrite only unique pixels

VIDRWVisual Image DirectoryThumbnailed directory generation.

WINRWSelect or display image to Windows screenWindows only.

XRWSelect or display image to X server screen

XCRCanvas image of specified colorBackward compatible alias for canvas:.

## Built-in Images

Embedded sample images referenceable via magick:name.

 Tag Mode Description Notes

GRANITER128x128 granite texture patternGranite texture asset.

LOGORImageMagick Logo, 640x480Standard logo asset.

NETSCAPERNetscape 216 color cube image, 216x144Used with map option for web-safe colors.

ROSERPicture of a rose, 70x46Classic sample image.

WIZARDRImageMagick Wizard, 480x640Wizard mascot asset.

## Built-in Patterns

Embedded patterns referenceable via pattern:name, controlled by the -size option.

 Tag Mode Description & Dimensions

BRICKSRBrick pattern, 16x16

CHECKERBOARDRCheckerboard pattern, 30x30

CIRCLESRCircles pattern, 16x16

CROSSHATCHRCrosshatch pattern, 8x4

CROSSHATCH30RCrosshatch pattern at 30 degrees, 8x4

CROSSHATCH45RCrosshatch pattern at 45 degrees, 8x4

FISHSCALESRFish scales pattern, 16x8

GRAY0 through GRAY100RIntensity gray patterns (0% to 100%), 32x32

HEXAGONSRHexagon pattern, 30x18

HORIZONTALRHorizontal line pattern, 8x4

HORIZONTAL2RHorizontal line pattern, 8x8

HORIZONTAL3RHorizontal line pattern, 9x9

HORIZONTALSAWRHorizontal saw-tooth pattern, 16x8

HS_BDIAGONALRBackward diagonal line pattern (45° slope), 8x8

HS_CROSSRCross line pattern, 8x8

HS_DIAGCROSSRDiagonal line cross pattern (45° slope), 8x8

HS_FDIAGONALRForward diagonal line pattern (45° slope), 8x8

HS_HORIZONTALRHorizontal line pattern, 8x8

HS_VERTICALRVertical line pattern, 8x8

LEFT30RForward diagonal pattern (30° slope), 8x4

LEFT45RForward diagonal line pattern (45° slope), 8x8

LEFTSHINGLERLeft shingle pattern, 24x24

OCTAGONSROctagons pattern, 16x16

RIGHT30RBackward diagonal line pattern (30°), 8x4

RIGHT45RBackward diagonal line pattern (30°), 8x8

RIGHTSHINGLERRight shingle pattern, 24x24

SMALLFISHSCALESRSmall fish scales pattern, 8x8

VERTICALRVertical line pattern, 8x8

VERTICAL2RVertical line pattern, 8x8

VERTICAL3RVertical line pattern, 9x9

VERTICALBRICKSRVertical brick pattern, 16x16

VERTICALLEFTSHINGLERVertical left shingle pattern, 24x24

VERTICALRIGHTSHINGLERVertical right shingle pattern, 24x24

VERTICALSAWRVertical saw-tooth pattern, 8x16

## Embedded Image Profiles

Identifiers used to add, remove, and save embedded metadata profiles (TIFF, JPEG, PDF).

 Tag Mode Description Notes

8BIMRWPhotoshop resource format (binary)

8BIMTEXTRWPhotoshop resource format (ASCII)ASCII representation of 8BIM.

APP1RWRaw application information

APP1JPEGRWRaw JPEG binary dataProfile in JPEG wrapper.

ICCRWInternational Color Consortium color profile (ICM)Read via -profile option.

IPTCRWIPTC Newsphoto (binary)Read via -profile option.

IPTCTEXTRWIPTC Newsphoto (ASCII)ASCII representation of IPTC.

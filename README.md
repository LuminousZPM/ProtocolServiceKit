# ProtocolServiceManger

[![CI Status](https://img.shields.io/travis/DevdragonLi/ProtocolServiceManger.svg?style=flat)](https://travis-ci.org/DevdragonLi/ProtocolServiceManger)
[![Version](https://img.shields.io/cocoapods/v/ProtocolServiceManger.svg?style=flat)](https://cocoapods.org/pods/ProtocolServiceManger)
[![License](https://img.shields.io/cocoapods/l/ProtocolServiceManger.svg?style=flat)](https://cocoapods.org/pods/ProtocolServiceManger)
[![Platform](https://img.shields.io/cocoapods/p/ProtocolServiceManger.svg?style=flat)](https://cocoapods.org/pods/ProtocolServiceManger)


> A simple and efficient  Protocol<=>Service 

## Example

To run the example project, clone the repo, and run `pod install` from the Example directory first.

- AccountBusiness <=> PlayBusiness 

```

  VIP和播放业务复杂后，只公开Protocol文件决定业务对外能力
  组件交互：从VIP业务来校验当前用户是否VIP，进而决定是否可以触发播放业务执行播放

    Class <LFLVipProtocol> vipService = ServiceClassWithProtocol(LFLVipProtocol);
    if (vipService && [vipService isCurrentUserVipStatus]) {
        Class <LFLPlayProtocol> playService = ServiceClassWithProtocol(LFLPlayProtocol);
        [playService playMiniVideo];
        
    } else {
        NSLog(@"Error:LFLVipProtocol notfound service Class");
    }

```

- 对外业务能力如果未实现，编译期触发会触发断言处，便于发现问题。

- recommended convention

	- `XXX`Service

	- `XXX`Protocol


## Installation

ProtocolServiceManger is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'ProtocolServiceManger'
```

## Author

DevdragonLi, dragonLi_52171@163.com

## License

ProtocolServiceManger is available under the MIT license. See the LICENSE file for more info.
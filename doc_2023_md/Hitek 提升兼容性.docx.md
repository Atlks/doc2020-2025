Hitek 提升兼容性


Try catch ,,判空模式

global['log_err'] = log_err
global['log_info'] = log_info

try {
   window['log_info'] = log_info
} catch (e) {
}


Nullsafe调用模式

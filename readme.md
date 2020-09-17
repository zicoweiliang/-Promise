class Promise2 {
succeed = null
fail = null
state = 'pending' resolve(result) {
setTimeout(() => {
this.state = 'fulfilled' this.succeed(result)
})
}
reject(reason) {
setTimeout(() => {
this.state = 'rejected' this.fail(reason)
})
}
constructor(fn) {
fn(this.resolve.bind(this), this.reject.bind(this))
}
then(succeed, fail) {
this.succeed = succeed
this.fail = fail
}
}
new Promise2((resolve, reject) => {
console.log('fn run...')
setTimeout(() => {
if (Math.random() > 0.5) {
resolve(100)
} else {
reject('失败')
}
}, 1000)
}).then(n => {
console.log(n)
}, reason => {
console.log(reason)
})

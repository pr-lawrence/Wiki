https://docs.angularjs.org/api/ng/directive/input

ng-maxlength, ng-minlength 를 사용하면 쉽게 폼 벨리데이션을 할 수 있다.

```
<script>
   angular.module('inputExample', [])
     .controller('ExampleController', ['$scope', function($scope) {
       $scope.user = {name: 'guest', last: 'visitor'};
     }]);
</script>
<div ng-controller="ExampleController">
  <form name="myForm">
    <label>
       User name:
       <input type="text" name="userName" ng-model="user.name" required>
    </label>
    <div role="alert">
      <span class="error" ng-show="myForm.userName.$error.required">
       Required!</span>
    </div>
    <label>
       Last name:
       <input type="text" name="lastName" ng-model="user.last"
       ng-minlength="3" ng-maxlength="10">
    </label>
    <div role="alert">
      <span class="error" ng-show="myForm.lastName.$error.minlength">
        Too short!</span>
      <span class="error" ng-show="myForm.lastName.$error.maxlength">
        Too long!</span>
    </div>
  </form>
  <hr>
  <tt>user = {{user}}</tt><br/>
  <tt>myForm.userName.$valid = {{myForm.userName.$valid}}</tt><br/>
  <tt>myForm.userName.$error = {{myForm.userName.$error}}</tt><br/>
  <tt>myForm.lastName.$valid = {{myForm.lastName.$valid}}</tt><br/>
  <tt>myForm.lastName.$error = {{myForm.lastName.$error}}</tt><br/>
  <tt>myForm.$valid = {{myForm.$valid}}</tt><br/>
  <tt>myForm.$error.required = {{!!myForm.$error.required}}</tt><br/>
  <tt>myForm.$error.minlength = {{!!myForm.$error.minlength}}</tt><br/>
  <tt>myForm.$error.maxlength = {{!!myForm.$error.maxlength}}</tt><br/>
</div>
```

그러나 ng-modal에 값을 지워버리는 것 같은 상황이 있다!
이런 상황에서 7이 넘어가면 vm.name의 값을 지워버리는 것 같다. 자세하게 알아볼 것.


```
<input ng-modal="vm.name" ng-maxlength=7 />
```

<template>
    <div class="login">
        <img alt="logo" src="../assets/elnino.png">
        <h2>Sign Up</h2>
        <div>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" required>
        </div>
        <div>
            <label for="password">Create Password:</label>
            <input type="password" id="password" name="password" required>
        </div>
        <div>
            <label for="confirm-password">Confirm Password:</label>
            <input type="password" id="confirm-password" name="confirm-password" required>
        </div>
        <button type="submit">회원가입</button>
    </div>
</template>

<script>
export default {
  name: 'LoginView'
}
</script>
